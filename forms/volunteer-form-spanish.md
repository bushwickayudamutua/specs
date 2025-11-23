# Formulario de Registro de Voluntarios BAM - Español

**URL del Formulario:** https://forms.fillout.com/t/gXcSW6N8F1us
**URL de la Página:** https://bushwickayudamutua.com/volunteer/

---

## Campos del Formulario

### Sección 1: Introducción

#### 1. Título
**Tipo:** Encabezado
**Contenido:** Registro Voluntario

---

### Sección 2: Información de Contacto

#### 2. Encabezado de Sección
**Etiqueta:** Información del Contacto
**Tipo:** Texto

---

#### 3. Nombre
**Etiqueta:** Nombre
**Tipo:** Respuesta corta
**Requerido:** Sí

---

#### 4. Número de Teléfono
**Etiqueta:** Número de Teléfono
**Tipo:** Número de teléfono
**Requerido:** Sí
**País por defecto:** US

---

#### 5. Correo Electrónico
**Etiqueta:** Correo Electrónico
**Tipo:** Email
**Requerido:** Sí
**Validación:** Debe ser formato de email válido

---

### Sección 3: Sobre Ti

#### 6. Encabezado de Sección
**Etiqueta:** Cuéntanos un poco sobre ti
**Tipo:** Texto

---

#### 7. Idiomas que Hablas
**Etiqueta:** ¿Qué idiomas hablas?
**Tipo:** Casillas de verificación (Selección múltiple)
**Requerido:** Sí
**Predeterminado:** Spanish / Español

**Opciones:**
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

#### 8. Otros Idiomas
**Etiqueta:** ¿Cuál otro(s) idioma(s)?
**Tipo:** Respuesta corta
**Requerido:** Sí (cuando visible)
**Condición:** Se muestra si "Other / Otro" está seleccionado en Idiomas

---

#### 9. Grupos de Trabajo
**Etiqueta:** ¿En qué tipo de grupos te gustaría ayudar?
**Tipo:** Casillas de verificación (Selección múltiple)
**Requerido:** Sí

**Opciones:**
- Community Outreach (callers) / Alcance Comunitario (Llamadores)
- Finance, Accounting / Finanzas, Contabilidad
- Food Coordination & Food Partnerships / Coordinación y Consorcio de Alimentos
- Fundraising and Event Planning / Recaudación de Fondos y planificación de eventos
- Community Building / Fomentando Comunidad
- One-time volunteer this time / Solo voluntariado una vez
- Tech and data support / Soporte técnico y de datos
- Social Media, PR / Redes Sociales, Relaciones Públicas
- Furniture Coordination / Coordinación de muebles
- Social Services / Servicios Sociales

---

#### 10. Tipo de Soporte Técnico
**Etiqueta:** ¿Qué soporte técnico puedes dar?
**Tipo:** Casillas de verificación (Selección múltiple)
**Requerido:** Sí (cuando visible)
**Condición:** Se muestra si "Tech and data support / Soporte técnico y de datos" está seleccionado en Grupos de Trabajo

**Opciones:**
- Data cleaning and analysis / Limpieza y análisis de datos
- Programming and automation / Programación y automatización
- NYC Mesh Installations / Instalaciones para NYC Mesh

---

#### 11. Capacidad de Levantamiento
**Etiqueta:** Puedo levantar 50 libras
**Tipo:** Opción múltiple
**Requerido:** No
**Descripción:** This is necessary for some roles in the food distribution team.

**Opciones:**
- Yes / Sí
- No / No

---

### Sección 4: Acuerdo de Voluntariado

#### 12. Encabezado de Sección
**Etiqueta:** Acuerdo de Voluntariado
**Tipo:** Texto

---

#### 13. Declaración de Salud COVID-19
**Etiqueta:** Soy asintomático y no conozco a nadie que haya sido expuesto o haya sido diagnosticado con COVID-19
**Tipo:** Casilla de verificación
**Requerido:** Sí

---

#### 14. Normas de Privacidad y Seguridad
**Etiqueta:** He leído, y seguiré todas las normas de privacidad y seguridad listadas a continuación si me ofrezco como voluntario.
**Tipo:** Casilla de verificación
**Requerido:** Sí
**Enlaces:**
- Normas de privacidad: https://bushwickayudamutua.com/privacy/
- Normas de seguridad: https://bushwickayudamutua.com/safety/

---

#### 15. Acuerdos Comunitarios
**Tipo:** Párrafo informativo
**Requerido:** No

**Contenido:**

**No Jerarquía:**
- Trabajamos colaborativamente compartiendo responsabilidad y poder.
- Actuamos con transparencia y nos comunicamos con todos los afectados.
- Enseñamos lo que sabemos y aprendemos lo que no.
- Expresamos preocupaciones cuando vemos a alguien actuando contrario a nuestros valores.
- Somos colectivamente responsables de nuestro trabajo y la seguridad de la comunidad que servimos.

**Abolición:**
- Practicamos alternativas al cuidado policial y carcelario. Esta es una zona libre de policía.
- No toleramos ninguna forma de opresión.
- Compartimos nuestras visiones de abolición creativamente.

**Crecimiento:**
- Abordamos los conflictos directamente pero con respeto.
- Somos honestos sobre nuestra capacidad y pedimos ayuda cuando la necesitamos.
- Respetamos y acomodamos las diferentes capacidades de nuestros compañeros.
- Nos responsabilizamos mutuamente mientras damos gracia.

---

#### 16. Aceptación de Acuerdos Comunitarios
**Etiqueta:** He leído y acepto los acuerdos comunitarios anteriores
**Tipo:** Casilla de verificación
**Requerido:** Sí

---

### Sección 5: Verificación

#### 17. CAPTCHA
**Etiqueta:** Por favor verifique su identidad a través de CAPTCHA
**Tipo:** Captcha
**Requerido:** Sí

---

#### 18. Botón de Envío
**Tipo:** Botón
**Muestra Botón de Retroceso:** Sí

---

## Página de Agradecimiento

**Mensaje:** Gracias

**Contenido:** Confirmación de envío.

---

## Resumen de Lógica Condicional

| Condición | Campo Mostrado |
|-----------|----------------|
| "Other / Otro" seleccionado en Idiomas | Campo de Otros Idiomas (#8) |
| "Tech and data support" seleccionado en Grupos de Trabajo | Campo de Tipo de Soporte Técnico (#10) |
