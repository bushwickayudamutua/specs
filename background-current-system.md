# BAM Mutual Aid System - Current System Background

This document describes the existing system architecture and workflows. It serves as reference for understanding the current state before improvements.

---

## 1. System Overview

Bushwick Ayuda Mutua (BAM) operates a mutual aid system that manages intake requests, distribution events, and volunteer coordination through a combination of Airtable, Digital Ocean functions, and manual processes.

### Technology Stack
- **Database:** Airtable
- **Automation:** Digital Ocean Functions
- **SMS:** Dialpad API
- **Email:** Mailjet
- **Address Validation:** Google Maps API + NYC Planning Labs
- **File Storage:** Digital Ocean Spaces (S3-compatible)
- **Forms:** Fillout (multi-language)

### GitHub Repository
- **Repo:** https://github.com/bushwickayudamutua/bam-automation
- **Entry Point:** `functions/project.yml`
- **API Docs:** https://airtable.com/appjIo54Z8MWrqhlI/api/docs

---

## 2. Current Outreach Flowchart

![BAM Outreach Flowchart](./bam-outreach-flowchart.png)

*Current outreach process: automated text blasts, retry logic (3x text, then call, then email), timeout handling*

---

## 3. Existing Automation Functions

### Scheduled Jobs (Cron)

| Function | Schedule | Purpose |
|----------|----------|---------|
| `UpdateWebsiteRequestData` | Hourly | Publishes open request counts to website JSON |
| `DedupeAirtableViews` | Daily (10:33 PM ET) | Deduplicates records by phone across 23 views |
| `UpdateMailjetLists` | Daily | Syncs contacts to Mailjet email lists |
| `SnapshotAirtableViews` | Daily | Backs up modified records to S3 |

### Web-Triggered Functions

| Function | Purpose |
|----------|---------|
| `send_dialpad_sms` | Sends SMS text blasts via Dialpad API |
| `send_dialpad_sms` (V2) | SMS using new Household ORM model |
| `consolidate_eg_requests` | Consolidates requests when household needs multiple items |
| `timeout_eg_requests` | Times out old unfulfilled requests when newer ones fulfilled |
| `update_field_value` | Bulk updates field for multiple phone numbers |
| `/clean-record` API | Validates/normalizes phone, email, address |

### External Service Integrations

| Service | Purpose |
|---------|---------|
| Airtable | Primary database |
| Dialpad | SMS messaging |
| Mailjet | Email list management |
| Google Maps | Address normalization |
| NYC Planning Labs | Geospatial address lookup |
| Digital Ocean Spaces | File storage/CDN for snapshots |

---

## 4. Current Airtable Schema

### Tables Overview

#### Households
Primary table for recipient households.

| Field | Type | Description |
|-------|------|-------------|
| Name | singleLineText | Household name |
| ID | autoNumber | Unique identifier |
| Phone Number | phoneNumber | Primary contact (unique key) |
| Invalid Phone Number? | checkbox | Validation flag |
| Int'l Phone Number? | checkbox | International number flag |
| Email | email | Contact email |
| Email Error | singleLineText | Validation error message |
| Languages | multipleSelects | Preferred languages |
| Notes | richText | Free-form notes |
| Requests | multipleRecordLinks | Link to Requests table |
| Open Request Types | multipleLookupValues | Lookup of open request types |
| Delivered Request Types | multipleLookupValues | Lookup of delivered types |
| Social Service Requests | multipleRecordLinks | Link to Social Service Requests |
| Open Social Service Request Types | multipleLookupValues | Lookup of open SS types |
| Created At | createdTime | Record creation time |
| Updated At | lastModifiedTime | Last modification time |
| Date of Oldest Fulfillable Request | rollup | Earliest open request date |
| Legacy First/Last Date Submitted | date | Migration fields |
| Form Submissions | multipleRecordLinks | Link to form submissions |
| Appointment Date | date | Scheduled appointment |
| Appointment Time | singleSelect | Time slot (11:00 AM, 11:30 AM) |
| Appointment Status | singleSelect | Booked/Checked-in/Missed |
| Last Texted | date | Last SMS outreach date |

#### Requests
Individual goods/service requests linked to households.

| Field | Type | Description |
|-------|------|-------------|
| Label | formula | Display label (from Type) |
| Type | singleSelect | Request type (trilingual) |
| Household | multipleRecordLinks | Link to Households |
| Status | singleSelect | Open/Timeout/Delivered |
| Notes | multilineText | Request-specific notes |
| Updated At | lastModifiedTime | Last modification |
| Status Last Updated At | lastModifiedTime | When status changed |
| Legacy Date Submitted | date | Migration field |
| Request Opened At | formula | Effective open date |
| Processing Date | formula | Auto-calculated expiry (14/30 days) |
| Street Address | singleLineText | Delivery address |
| City, State | singleLineText | Location |
| Zip Code | number | Postal code |
| Geocode | singleLineText | Geo coordinates |
| Address | singleLineText | Formatted address |
| Phone Number (from Household) | multipleLookupValues | Lookup |
| Last texted (from Household) | multipleLookupValues | Lookup |

**Processing Date Formula:**
- Status changed to Delivered: +14 days (or +30 for Pots & Pans)
- Status changed to Timeout: +14 days

#### Social Service Requests
Separate table for social services (different from goods).

| Field | Type | Description |
|-------|------|-------------|
| Label | formula | Display label |
| Phone Number (from Household) | multipleLookupValues | Contact lookup |
| Type | singleSelect | Service type (12 options) |
| Status | singleSelect | Open/Timeout/Delivered |
| Household | multipleRecordLinks | Link to Households |
| Internet Access | multipleSelects | Current internet situation |
| Roof Accessible? | checkbox | For internet installation |
| Address fields | various | Location data |
| Status Last Updated At | lastModifiedTime | Status change time |
| Notes | multilineText | Service notes |
| Request Opened At | formula | Effective open date |
| Processing Date | formula | +14 days after status change |

#### Distros
Distribution event tracking.

| Field | Type | Description |
|-------|------|-------------|
| Date & Time | dateTime | Event date/time |
| Location | singleLineText | Venue |
| Duration | duration | Event length |
| Appointments | singleLineText | Appointment count/details |
| Notes | multilineText | Event notes |

#### Fulfilled Request Count
Aggregated metrics per date (50+ columns for all request types).

#### Assistance Request Form Submissions
Raw form intake data from Fillout forms.

---

## 5. Request Type Categories

### Essential Goods
- **Toiletries:** Soap, Pads, Baby Diapers, Adult Diapers
- **Household:** Clothing, School Supplies, Stroller, Pet Food

### Kitchen Items
- Pots & Pans, Plates, Cups, Utensils, Microwave, Coffee Maker, Blender

### Furniture
- **Beds:** Crib through King (mattress/frame options)
- Sofa, Dresser, Desk, Coffee Table, Chairs, Storage, Dining Table, Fridge, AC

### Food Requests
- Groceries, Hot meals

### Social Services
- Housing, Health Insurance, English Classes, Transportation
- Tenant legal, In-school services, Tutoring, Business support
- Internet, Food benefits, Child disability, Pet assistance

---

## 6. Multi-Language Support

### Supported Languages
- English, Spanish, Mandarin, Cantonese, Toishanese
- Quechua, Portuguese, Haitian Creole, Tagalog, Arabic, French

### Trilingual Format
All request names stored in format:
```
"Jabón & Productos de baño / Soap & Shower Products / 肥皂和淋浴用品"
```

---

## 7. Current Operational Metrics

- **Distribution frequency:** 3 appointment-based distributions per week
- **Appointments per distribution:** ~60
- **Outreach target:** 240 people (25% hit rate)
- **Request expiration:** 14 days (30 days for Pots & Pans)

---

## 8. Known Issues & Technical Debt

### Data Privacy
- Addresses stored in plain text for furniture/delivery requests (hashing would break logistics)
- PII not properly anonymized after fulfillment

### Edge Cases
- Multiple households sharing same phone number causes deduplication issues
- Multiple phone numbers per household creates duplicate households
- Language matching between volunteers and recipients is manual

### Concessions
- 14-day expiration window may be too short for some needs
- Text blast targeting requires manual view creation
- Post-distro inventory is informal text-based reporting

---

## 9. Form URLs by Language

| Language | Form URL |
|----------|----------|
| English | https://forms.fillout.com/t/ivajQbwoWxus |
| Spanish | https://forms.fillout.com/t/sevuKn32WBus |
| Chinese (Traditional) | https://forms.fillout.com/t/docSKMdPyBus |
| French | https://forms.fillout.com/t/dDXKMJ1Fjqus |
| Arabic | https://forms.fillout.com/t/fAM7NKL8LPus |

---

## 10. Links & References

- **Airtable API:** https://airtable.com/appjIo54Z8MWrqhlI/api/docs
- **Automation repo:** https://github.com/bushwickayudamutua/bam-automation
- **Entry point:** `functions/project.yml`
- **SMS endpoint:** `/send_dialpad_sms`
