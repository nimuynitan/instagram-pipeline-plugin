---
name: visual-brief
description: This skill should be used when the user needs to create a detailed visual brief for each Instagram carousel slide — defining the background photo concept for DALL-E 3, the Photoshop layer structure, exact HEX colors, text positioning, and design specifications for the designer. Trigger when creating visual direction for Instagram posts, or when part of the instagram-pipeline.
---

# Skill: visual-brief

## Objetivo
Producir dos outputs en paralelo:
1. **Prompts para DALL-E 3** — descripción precisa del fondo fotográfico de cada slide (sin texto, listo para generar)
2. **Brief Photoshop** — especificaciones exactas para que el diseñador arme el slide final encima de la imagen generada

## Identidad visual de Universidad Uk
Leer los valores exactos desde `~/.claude/instagram-pipeline/style-guide.md`. Si el archivo tiene los valores completados, usarlos. Si no, usar estos valores de referencia (aproximados — el diseñador debe confirmar):

| Elemento | Valor de referencia |
|---|---|
| Color titular (amarillo/naranja bold) | #FFB800 |
| Color subtítulo | #FFFFFF |
| Color texto de apoyo | #FFFFFF |
| Color badge | #E85D04 |
| Overlay oscuro sobre foto | rgba(0, 0, 0, 0.55) |
| Logo: posición | Esquina superior derecha |
| Logo: margen | 32px desde bordes |
| Formato feed | 1080 x 1080 px |
| Formato story | 1080 x 1920 px |

## Proceso

### 1. Prompts para DALL-E 3 (por slide)

Para cada slide, escribir un prompt que:
- Describe la fotografía de fondo ideal para el tema del slide
- Especifica que NO debe contener texto, letras, palabras ni números
- Define el mood y la paleta visual (oscuro, cinematográfico, profesional)
- Indica el sujeto principal y la composición (espacio libre para texto superpuesto)
- Está en inglés (DALL-E responde mejor en inglés)

**Estructura del prompt:**
```
[Descripción del sujeto y escenario], [mood y iluminación], [composición con espacio libre para texto], professional photography, cinematic lighting, dark atmospheric background, no text, no words, no letters, photorealistic, 4K quality
```

**Ejemplos por tipo de contenido:**
- Carrera de ingeniería: "Two engineers in hard hats reviewing digital blueprints on a tablet in a modern industrial facility, dramatic blue tones, left side clear for text overlay"
- Efeméride tecnológica: "Vintage communication devices arranged on a wooden desk — rotary phone, radio, early computer — warm moody lighting, dark background"
- Tip de estudio: "Young professional studying on a laptop in a modern home office at night, warm desk lamp, focused atmosphere, right side clear for text"

### 2. Brief Photoshop (por slide)

Para cada slide, especificar:

**Capas en orden (de abajo hacia arriba):**
1. Imagen de fondo (generada por DALL-E 3)
2. Overlay oscuro: capa de color negro, opacidad 55%, modo Normal
3. Texto de apoyo (si aplica): posición, tamaño, color
4. Subtítulo: posición, tamaño, color
5. Titular: posición, tamaño, color, peso
6. Badge de país (si aplica): rectángulo naranja + texto
7. Logo Uk: esquina superior derecha, tamaño definido

**Posicionamiento de texto:**
- Zona segura feed: margen interno de 60px en todos los bordes
- Zona segura story: margen interno de 80px laterales, 160px arriba y abajo (evitar zonas de UI de Instagram)
- Alineación del texto: izquierda en la mayoría de casos (como en los ejemplos de referencia)
- El texto principal ocupa el tercio inferior o el centro-izquierda de la imagen

## Output esperado

Guardar en `posts/{slug}/visual-brief.md`:

```markdown
# Visual Brief: {tema} — {país}

## Identidad visual aplicada
[HEX colors + fuentes usados, leídos del style-guide]

---

## Slide 1

### Prompt DALL-E 3
**Feed (1024x1024):**
[prompt en inglés]

**Story (1024x1792):**
[mismo concepto adaptado a vertical — más espacio en la parte superior e inferior]

### Brief Photoshop
**Capas:**
1. Fondo: slide-1-feed.png
2. Overlay: negro, 55% opacidad
3. Titular: "[texto]" — [fuente], [tamaño]px, bold, color [HEX], posición [X,Y]
4. Subtítulo: "[texto]" — [fuente], [tamaño]px, regular, #FFFFFF, posición [X,Y]
5. Texto apoyo: "[texto]" — [fuente], [tamaño]px, light, #FFFFFF, posición [X,Y]
6. Badge: rectángulo [HEX], texto "[país + año]", posición [X,Y]
7. Logo: logo.png, [ancho]px, esquina superior derecha, margen 32px

---

## Slide 2
[misma estructura]

...

## Slide 5
[misma estructura]

---

## Notas para el diseñador
- [cualquier indicación especial sobre consistencia entre slides]
- [si el logo está disponible en ~/.claude/instagram-pipeline/logo.png o debe agregarse manualmente]
```
