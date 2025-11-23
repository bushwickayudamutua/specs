# BAM Volunteer Sign Up Form - English

**Form URL:** https://forms.fillout.com/t/oNNQK8ogapus
**Page URL:** https://bushwickayudamutua.com/volunteer/

---

## Form Fields

### Section 1: Introduction

#### 1. Title
**Type:** Header
**Content:** Volunteer Sign Up

---

#### 2. Introduction
**Type:** Informational text
**Content:** Describes BAM and assures confidentiality of volunteer information.

---

### Section 2: Contact Information

#### 3. Section Header
**Label:** Contact Information
**Type:** Text

---

#### 4. First Name
**Label:** First Name
**Type:** Short Answer
**Required:** Yes

---

#### 5. Phone Number
**Label:** Phone Number
**Type:** Phone Number
**Required:** Yes
**Default Country:** US

---

#### 6. Email
**Label:** Email
**Type:** Email
**Required:** Yes
**Validation:** Must be valid email format

---

### Section 3: About You

#### 7. Section Header
**Label:** Tell us a bit about yourself
**Type:** Text

---

#### 8. Languages Spoken
**Label:** What language(s) do you speak?
**Type:** Checkboxes (Multiple selection)
**Required:** Yes
**Default:** English / Inglés

**Options:**
- English / Inglés
- Spanish / Español
- Mandarin / Mandarina
- Cantonese / Cantonesa
- Quechua Dialect / Quechua el dialecto
- Tagalog / Tagalo
- French / Francés
- Italian / Italiano
- Kreyol / Criollo
- Other / Otro

---

#### 9. Other Languages
**Label:** What other language(s)?
**Type:** Short Answer
**Required:** Yes (when visible)
**Condition:** Shows only if "Other / Otro" is selected in Languages

---

#### 10. Working Groups
**Label:** What working groups are you interested in joining?
**Type:** Checkboxes (Multiple selection)
**Required:** Yes

**Options:**
- Community Outreach (callers) / Alcance Comunitario (Llamadores)
- Finance, Accounting / Finanzas, Contabilidad
- Food Coordination & Food Partnerships / Coordinación y Consorcio de Alimentos
- Fundraising and Event Planning / Recaudación de Fondos y planificación de eventos
- Community Building / Fomentando Comunidad
- One-time volunteer this time / Solo voluntariado una vez
- Tech and data support / Soporte técnico y de datos
- Social Media, PR / Redes Sociales, Relaciones Públicas
- Furniture Coordination / Coordinacion de muebles
- Social Services / Servicios Sociales

---

#### 11. Tech Support Type
**Label:** What type of tech support are you interested in?
**Type:** Checkboxes (Multiple selection)
**Required:** Yes (when visible)
**Condition:** Shows only if "Tech and data support / Soporte técnico y de datos" is selected in Working Groups

**Options:**
- Data cleaning and analysis / Limpieza y análisis de datos
- Programming and automation / Programación y automatización
- NYC Mesh Installations / Instalaciones para NYC Mesh

---

#### 12. Lifting Capacity
**Label:** I can lift 50 pounds
**Type:** Multiple Choice
**Required:** No
**Caption:** This is necessary for some roles on the food distribution team.

**Options:**
- Yes / Sí
- No / No

---

### Section 4: Volunteer Agreements

#### 13. Section Header
**Label:** Volunteer Agreements
**Type:** Text

---

#### 14. COVID-19 Health Declaration
**Label:** I am asymptomatic and as far as I am aware and I have not recently been exposed to anyone tested positive with COVID-19.
**Type:** Checkbox
**Required:** Yes

---

#### 15. Privacy & Safety Guidelines
**Label:** I have read and will adhere to the privacy and safety guidelines listed below should I volunteer.
**Type:** Checkbox
**Required:** Yes
**Links:**
- Privacy guidelines: https://bushwickayudamutua.com/privacy/
- Safety guidelines: https://bushwickayudamutua.com/safety/

---

#### 16. Community Agreements
**Type:** Informational Paragraph
**Required:** No

**Content:**

**No Hierarchy:**
- We work collaboratively by sharing responsibility and power.
- We act with transparency and communicate with all affected.
- We teach what we know and learn what we don't.
- We raise concerns when we see someone behaving contrary to our values.
- We are collectively responsible for our work and the safety of the community we serve.

**Abolition:**
- We practice alternatives to police and carceral care. This is a police-free zone.
- We do not tolerate any form of oppression.
- We share our visions of abolition with each other creatively.

**Growth:**
- We address conflict directly but respectfully.
- We are honest about our capacity and ask for help when needed.
- We respect and accommodate the varying capacities of our peers.
- We hold each other accountable while giving grace.

---

#### 17. Community Agreements Acceptance
**Label:** I have read and agree to the above community agreements.
**Type:** Checkbox
**Required:** Yes

---

### Section 5: Verification

#### 18. CAPTCHA
**Label:** Please verify yourself via CAPTCHA
**Type:** Captcha
**Required:** Yes

---

#### 19. Submit Button
**Type:** Button
**Shows Back Button:** Yes

---

## Thank You Page

**Message:** Thank you

**Content:** Confirmation of submission with Fillout branding.

---

## Conditional Logic Summary

| Condition | Field Shown |
|-----------|-------------|
| "Other / Otro" selected in Languages | Other Languages field (#9) |
| "Tech and data support" selected in Working Groups | Tech Support Type field (#11) |
