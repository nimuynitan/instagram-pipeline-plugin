---
name: visual-brief
description: This skill should be used when the user needs to create a detailed visual brief for each Instagram carousel slide — defining the background photo concept for GPT Image 2, the Photoshop layer structure, exact HEX colors, text positioning, and design specifications for the designer. Trigger when creating visual direction for Instagram posts, or when part of the instagram-pipeline.
---

# Skill: visual-brief

## Objetivo
Producir dos outputs en paralelo:
1. **Prompts para GPT Image 2** — descripción precisa del fondo fotográfico de cada slide (sin texto, listo para generar)
2. **Brief Photoshop** — especificaciones exactas para que el diseñador arme el slide final encima de la imagen generada

## Identidad visual de Universidad Uk
Leer los valores exactos desde `~/.claude/instagram-pipeline/style-guide.md`.

Valores confirmados de marca:
| Elemento | Valor |
|---|---|
| Color titular | #FF671B (naranja Uk) |
| Color subtítulo | #FFFFFF |
| Color texto de apoyo | #FFFFFF |
| Color badge | #FF671B |
| Overlay sobre foto | rgba(0, 0, 0, 0.50) |
| Logo: posición | Esquina superior derecha |
| Logo: margen | 32px desde bordes |
| Formato feed | 1080 x 1080 px |
| Formato story | 1080 x 1920 px |

## Reglas de composición fotográfica (CRÍTICO)

Estas reglas son obligatorias en todos los prompts. El estilo de referencia del perfil @uk.universidad usa siempre:

### 1. Personas latinoamericanas siempre
- El sujeto principal es SIEMPRE una persona o grupo de personas latinoamericanas en contexto profesional o educativo
- NUNCA usar objetos simbólicos solos como sujeto principal (no balanzas de justicia solas, no libros solos, no edificios vacíos, no elementos abstractos)
- Las personas deben verse reales, contemporáneas, en situaciones cotidianas del mundo laboral o académico

### 2. Iluminación cálida y profesional — NO cinematográfica oscura
- Iluminación cálida, controlada, de estudio o de oficina moderna
- La foto debe ser clara y legible ANTES de aplicar el overlay
- El overlay oscuro lo aplica el diseñador encima — la foto no debe ser oscura por sí sola
- Paleta de tonos cálidos (ambar, dorado, tostado) o neutros profesionales
- Evitar: iluminación dramática extrema, backlit, siluetas, fondos totalmente negros

### 3. Composición con espacio para texto
- Sujeto posicionado en el tercio derecho o inferior de la imagen
- El tercio izquierdo o superior izquierdo queda relativamente despejado para el texto
- Si hay varias personas, agruparlas a un lado dejando espacio al otro
- Fondo desenfocado (bokeh) detrás de las personas para que el texto superpuesto sea legible

### 4. Escenarios según tipo de contenido
- **Carreras profesionales** (derecho, psicología, administración): oficina moderna, sala de reuniones, despacho profesional, espacio corporativo
- **Carreras creativas** (arte, comunicación, arquitectura): estudio creativo, espacio de diseño, entorno con elementos de la carrera
- **Efemérides** (días internacionales, fechas especiales): persona celebrando o trabajando en el contexto del tema
- **Tips/educación online**: persona estudiando con laptop en casa u oficina, ambiente cómodo y bien iluminado
- **Institucional**: grupo de personas diversas en contexto universitario o profesional

## Proceso

### 1. Prompts para GPT Image 2 (por slide)

**Estructura obligatoria del prompt:**
```
[Descripción de la persona: edad aproximada, género, vestimenta profesional, expresión], [acción que realiza], [escenario específico y concreto], warm professional lighting, [composición: sujeto en right/left third, opposite side clear for text overlay], shallow depth of field, bokeh background, no text, no words, no letters, photorealistic, 4K, professional photography
```

**Ejemplos correctos por tipo:**
- Derecho: "Latin American woman in her 30s wearing professional blazer, reviewing legal documents at a modern wooden desk, warm office lighting with city view in background, subject positioned on right third, left area clear for text overlay, shallow depth of field, no text, photorealistic, 4K"
- Educación online: "Young Latin American man in his late 20s smiling while working on laptop at a bright modern home office, warm natural light from window, positioned on right side, left third clear, bokeh background, no text, photorealistic, 4K"
- Efeméride profesional: "Latin American professional woman in her 40s standing confidently in a modern office hallway, warm ambient lighting, subject on right third leaving left side open for text, shallow depth of field, no text, photorealistic, 4K"

**Ejemplos INCORRECTOS (no usar):**
- ❌ "Scales of justice with digital circuit board background, dark cinematic lighting"
- ❌ "Ancient law books on mahogany desk, candlelight, dark atmospheric"
- ❌ "Stone colonial courtyard at dawn, no people, dramatic shadows"

### 2. Brief Photoshop (por slide)

**Capas en orden (de abajo hacia arriba):**
1. Imagen de fondo (generada por GPT Image 2)
2. Overlay negro, opacidad 50%, modo Normal
3. Texto de apoyo (si aplica): Poppins Light, blanco, zona inferior izquierda
4. Subtítulo: Montserrat SemiBold, #FFFFFF, debajo del titular
5. Titular: Montserrat ExtraBold, #FF671B, tercio inferior izquierdo
6. Badge de país: rectángulo #FF671B, texto blanco Montserrat SemiBold
7. Logo: logo.png, esquina superior derecha, ancho 120px, margen 32px

**Posicionamiento de texto:**
- Zona segura feed: margen mínimo 60px todos los bordes
- Zona segura story: margen 80px laterales, 160px arriba y abajo
- Alineación: izquierda siempre
- Bloque de texto: ocupa el tercio inferior izquierdo

## Output esperado

Guardar en `posts/{slug}/visual-brief.md`:

```markdown
# Visual Brief: {tema} — {país}

## Identidad visual aplicada
- Titular: Montserrat ExtraBold, #FF671B
- Subtítulo: Montserrat SemiBold, #FFFFFF
- Apoyo: Poppins Light, #FFFFFF
- Overlay: negro 50%
- Logo: logo.png, 120px, esquina superior derecha

---

## Slide 1

### Prompt GPT Image 2
**Feed (1024x1024):**
[prompt en inglés siguiendo estructura obligatoria]

**Story (1024x1536):**
[mismo concepto, composición adaptada a vertical: sujeto en tercio inferior, espacio libre arriba]

### Brief Photoshop
**Capas:**
1. Fondo: slide-1-feed.png
2. Overlay: negro, 50% opacidad
3. Titular: "[texto]" — Montserrat ExtraBold, 68px, #FF671B, posición: 60px desde izquierda, 780px desde arriba
4. Subtítulo: "[texto]" — Montserrat SemiBold, 40px, #FFFFFF, posición: 60px desde izquierda, 860px desde arriba
5. Texto apoyo: "[texto]" — Poppins Light, 26px, #FFFFFF, posición: 60px desde izquierda, 920px desde arriba
6. Badge: rectángulo #FF671B, texto "[país] [año]" Montserrat SemiBold 16px blanco, esquina superior derecha bajo el logo
7. Logo: logo.png, 120px ancho, esquina superior derecha, margen 32px

---

## Slide 2
[misma estructura]

...

## Slide 5
[misma estructura]

---

## Notas para el diseñador
- Logo disponible en: ~/.claude/instagram-pipeline/logo.png (PNG con fondo transparente)
- [cualquier indicación especial de consistencia entre slides]
```
