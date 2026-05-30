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

Estas reglas son obligatorias en todos los prompts. El estilo de referencia del perfil @uk.universidad es **lifestyle real y luminoso** — fotografía auténtica de personas jóvenes latinas en contextos cotidianos, NO estética corporativa oscura ni cinematográfica.

### 1. Personas latinas jóvenes siempre, en contexto cotidiano auténtico
- El sujeto principal es SIEMPRE una persona latina real, generalmente joven (20-40 años, ajustar según buyer persona de la carrera)
- Contextos cotidianos y auténticos: café, oficina moderna, casa/home office, campus universitario, exteriores urbanos, escritorio de estudio
- Las personas se ven espontáneas, relajadas, reales — sonriendo, concentradas, usando laptop o celular
- NUNCA usar objetos simbólicos solos como sujeto principal (no balanzas, no libros solos, no edificios vacíos, no elementos abstractos)
- Se permite el humor / situaciones identificables cuando el tema lo pide (ej: persona estresada entre papeles para un tema de organización)

### 2. Luz natural cálida y brillante — NO cinematográfica oscura
- Iluminación natural, cálida y LUMINOSA — luz de ventana, exteriores de día, ambientes bien iluminados
- La foto debe ser clara, brillante y alegre. NO oscura, NO dramática
- Evitar terminantemente: iluminación dramática extrema, backlit oscuro, siluetas, fondos negros, mood sombrío
- Paleta: tonos cálidos y naturales, ambientes acogedores, verde de plantas, madera, luz dorada suave
- Referencia mental: fotografía lifestyle de redes sociales / publicidad de producto tech, no foto de estudio corporativa

### 3. Composición con espacio para texto
- Sujeto posicionado en el tercio derecho o inferior de la imagen
- El tercio izquierdo o superior queda despejado para el texto superpuesto
- Fondo desenfocado (bokeh) detrás de la persona para que el texto sea legible
- Formato vertical preferido para historias; cuadrado para feed

### 4. Perfil del sujeto según buyer persona
Leer el perfil del sujeto definido en el `brief.md` (que viene del buyer persona de la carrera) y reflejarlo:
- **Edad**: usar la edad promedio del segmento Ingresantes de esa carrera (ej: Derecho ~38 años, Arquitectura ~33 años)
- **Género**: reflejar el predominante del persona (ej: si la carrera es 75% masculino, el sujeto principal es hombre)
- **Contexto de vida**: alinear el escenario con la situación laboral del persona (trabaja en oficina, estudia desde casa, emprende)

### 5. Escenarios según tipo de contenido
- **Carreras profesionales** (derecho, contabilidad, administración): persona joven-adulta trabajando en oficina luminosa, café con laptop, o home office ordenado
- **Carreras creativas** (diseño, comunicación, arquitectura, cine): persona en estudio creativo luminoso, espacio de trabajo con elementos de la carrera, exterior urbano
- **Efemérides**: persona del perfil celebrando o en su contexto cotidiano relacionado al tema
- **Tips / educación online**: persona estudiando con laptop en casa, café o campus, ambiente cómodo y bien iluminado, sonriente
- **Institucional**: persona joven latina diversa en contexto universitario o profesional luminoso

### 6. Referencias de estilo concretas (basadas en el material de marca)
Los prompts deben buscar imágenes con este feel:
- Mujer latina joven sonriendo con celular en un café luminoso, luz de ventana
- Hombre joven en oficina moderna y clara, expresión relajada y amable
- Persona estudiando con laptop en home office acogedor con plantas y luz natural
- Joven con laptop en exterior de campus, cielo azul, día soleado
- Persona usando celular sentada en escalinata urbana, luz de día

## Proceso

### 1. Prompts para GPT Image 2 (por slide)

**Estructura obligatoria del prompt:**
```
[Descripción de la persona: edad aproximada, género, vestimenta profesional, expresión], [acción que realiza], [escenario específico y concreto], warm professional lighting, [composición: sujeto en right/left third, opposite side clear for text overlay], shallow depth of field, bokeh background, no text, no words, no letters, photorealistic, 4K, professional photography
```

**Ejemplos correctos por tipo (estilo lifestyle luminoso):**
- Derecho (sujeto ~38, masculino): "Latin American man in his late 30s smiling confidently while working on laptop in a bright modern office, natural window light, plants in background, relaxed authentic expression, positioned on right third, left area clear for text overlay, shallow depth of field, bright airy lifestyle photography, no text, photorealistic, 4K"
- Educación online (sujeto joven): "Young Latin American woman around 28 studying with laptop at a cozy home office desk, warm natural light from window, plants and books in soft-focus background, genuine smile, positioned on right side, left third clear, bright lifestyle photography, no text, photorealistic, 4K"
- Tip de estudio: "Young Latin American man sitting on outdoor campus steps using smartphone, sunny day, blue sky, modern buildings bokeh background, casual relaxed mood, positioned on right, left side open for text, bright natural lifestyle photography, no text, photorealistic, 4K"

**Ejemplos INCORRECTOS (NUNCA usar):**
- ❌ "Scales of justice with digital circuit board, dark cinematic lighting"
- ❌ "Ancient law books on mahogany desk, candlelight, dark atmospheric"
- ❌ "Professional in dark dramatic office, moody lighting, deep shadows"
- ❌ Cualquier prompt con: dark, cinematic, dramatic lighting, moody, shadows, night, silhouette

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
