---
name: brief-analysis
description: This skill should be used when the user needs to analyze an Instagram post brief — interpreting the topic, defining the narrative angle, the 5-slide story arc, the target audience mindset, and the key message for each slide. Trigger when analyzing briefs for social media content creation, or when part of the instagram-pipeline. Always reads the style guide from ~/.claude/instagram-pipeline/style-guide.md before analyzing.
---

# Skill: brief-analysis

## Objetivo
Interpretar el brief editorial y definir la estrategia narrativa del carrusel antes de escribir cualquier copy. Un buen brief-analysis es lo que diferencia un carrusel genérico de uno que genera engagement real.

## Proceso

### 1. Interpretar el tema y el contexto
- ¿Qué quiere sentir o aprender el lector después de ver este carrusel?
- ¿Es una efeméride (la fecha importa), una carrera (el beneficio importa) o un tip (la utilidad importa)?
- ¿Qué emoción predomina: curiosidad, orgullo, urgencia, inspiración?

### 2. Definir el ángulo narrativo
No todos los temas se cuentan igual. Elegir uno:
- **Dato sorprendente** → hook con cifra o hecho que rompe expectativas
- **Pregunta provocadora** → hook con pregunta que el lector no sabe responder
- **Escenario identificable** → hook con situación que el lector vivió o teme
- **Antes/después** → contraste entre el estado actual y el posible
- **Lista de valor** → "X cosas que no sabías sobre Y"

### 3. Diseñar el arco de 5 slides
Cada slide tiene un rol específico en el carrusel:

| Slide | Rol | Objetivo |
|---|---|---|
| 1 | Hook / portada | Parar el scroll. Generar curiosidad para que deslicen |
| 2 | Contexto / problema | Establecer por qué esto importa |
| 3 | Desarrollo / valor 1 | Primer punto de valor concreto |
| 4 | Desarrollo / valor 2 | Segundo punto de valor o profundización |
| 5 | Cierre / CTA | Síntesis + acción clara |

Para efemérides: el slide 1 menciona la fecha, slides 2-4 desarrollan el tema con datos, slide 5 conecta con la propuesta de la universidad.

Para carreras: el slide 1 plantea el diferencial, slides 2-4 exploran salidas laborales o especialidades, slide 5 es el CTA de inscripción.

Para tips: el slide 1 es el hook con la promesa, slides 2-4 son los tips en sí, slide 5 es la síntesis + CTA.

### 4. Definir el mensaje clave de cada slide
Una oración por slide que resume qué tiene que quedarse grabado en el lector. Esta oración guía el copy-generation.

### 5. Considerar el contexto local
Si se especificó un país:
- ¿Hay datos locales relevantes para el tema?
- ¿El contexto económico o laboral del país cambia el ángulo?
- ¿Qué referencias locales resuenan mejor con la audiencia?

## Output esperado

Guardar en `posts/{slug}/brief.md`:

```markdown
# Brief: {tema} — {país}

## Parámetros
- Tema: 
- Formato: carrusel 5 slides
- Carrera: [si aplica]
- País: 
- Contexto adicional: 

## Ángulo narrativo
[Tipo elegido + justificación en 2 oraciones]

## Emoción predominante
[curiosidad / orgullo / urgencia / inspiración / otro]

## Arco narrativo

### Slide 1 — Hook
Rol: parar el scroll
Mensaje clave: [1 oración]

### Slide 2 — Contexto
Rol: establecer relevancia
Mensaje clave: [1 oración]

### Slide 3 — Valor 1
Rol: primer punto concreto
Mensaje clave: [1 oración]

### Slide 4 — Valor 2
Rol: segundo punto concreto
Mensaje clave: [1 oración]

### Slide 5 — Cierre
Rol: síntesis + CTA
Mensaje clave: [1 oración]

## Referencia de estilo aplicada
[Qué elementos del style-guide son más relevantes para este posteo]
```
