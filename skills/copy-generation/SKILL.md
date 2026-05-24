---
name: copy-generation
description: This skill should be used when the user needs to write complete Instagram carousel copy — slide text (headline, subtitle, supporting text), caption, hashtags, and CTA — following Universidad Uk's voice and visual hierarchy. Trigger when writing social media copy for Instagram, or when part of the instagram-pipeline. Always reads from the brief produced by brief-analysis.
---

# Skill: copy-generation

## Objetivo
Escribir el copy completo del carrusel: texto de cada slide con jerarquía visual definida, caption para Instagram, hashtags y CTA.

## Voz y tono (Universidad Uk — Instagram)
- **Directo y concreto**: cada slide dice una cosa, bien dicha. Sin relleno.
- **Cercano**: hablamos de tú, no de usted. Adultos que trabajan, no adolescentes.
- **Motivador sin exagerar**: inspiramos sin prometer lo que no podemos cumplir.
- **LATAM-first**: ejemplos y referencias de la región, no genéricos globales.
- **Sin voseo**: tuteo universal (puedes, tienes, decides — nunca podés, tenés, elegís).

## Reglas editoriales fijas
- Universidad siempre escrita **Universidad Uk** (k minúscula)
- Preguntas siempre con ¿ de apertura
- Sin frases vacías: "En el mundo actual...", "Hoy más que nunca..."
- Sin exclamaciones vacías: "¡Inscríbete ya!" → preferir: "El cupo es limitado. Reserva tu lugar."

## Estructura de copy por slide

### Texto en la gráfica (lo que ve el diseñador para poner sobre la imagen)
Cada slide tiene máximo 3 niveles de texto:

| Nivel | Rol | Caracteres máx. | Color en diseño |
|---|---|---|---|
| **Titular** | La idea principal del slide | 30-40 | Amarillo/naranja bold |
| **Subtítulo** | Complemento o gancho | 40-60 | Blanco bold |
| **Texto de apoyo** | Dato, pregunta o contexto | 60-80 | Blanco regular |

No todos los slides necesitan los 3 niveles. El slide 1 (hook) generalmente tiene solo titular + subtítulo.

### Caption de Instagram
- Primeras 2 líneas: el hook más fuerte (aparece antes del "ver más")
- Desarrollo: 3-5 líneas con el mensaje central
- CTA final: una acción clara y específica
- Longitud total: 150-300 caracteres antes del "ver más", 800-1200 en total
- Emojis: 2-4 máximo, usados con propósito (no decoración)

### Hashtags
- 8-12 hashtags por posteo
- Mix: 3-4 generales (#educaciononline #universidadonline), 3-4 de nicho (#carrerasenlinea #estudiaytrabaja), 2-3 de marca (#universidaduk #ukuiversidad)
- Adaptados al país si se especificó

## Proceso
1. Leer el brief completo de `posts/{slug}/brief.md`
2. Escribir el copy de cada slide siguiendo el arco narrativo definido
3. Verificar que el titular de cada slide funcione solo (sin necesitar contexto del anterior)
4. Escribir el caption completo
5. Generar los hashtags
6. Revisar que no haya voseo ni frases prohibidas

## Output esperado

Guardar en `posts/{slug}/copy.md`:

```markdown
# Copy: {tema} — {país}

---

## Slide 1 — Hook
**Titular:** [máx 40 chars — en gráfica, color amarillo/naranja]
**Subtítulo:** [máx 60 chars — en gráfica, color blanco bold]
**Texto de apoyo:** [opcional — máx 80 chars — blanco regular]
**Badge país:** [texto del badge naranja, ej: "Guatemala 2026"]

---

## Slide 2 — Contexto
**Titular:** 
**Subtítulo:** 
**Texto de apoyo:** 

---

## Slide 3 — Valor 1
**Titular:** 
**Subtítulo:** 
**Texto de apoyo:** 

---

## Slide 4 — Valor 2
**Titular:** 
**Subtítulo:** 
**Texto de apoyo:** 

---

## Slide 5 — Cierre + CTA
**Titular:** 
**Subtítulo:** 
**Texto de apoyo:** 
**CTA gráfica:** [texto del botón/acción en la imagen, si aplica]

---

## Caption

[Línea 1 del hook]
[Línea 2 del hook]

[Desarrollo]

[CTA]

---

## Hashtags

#hashtag1 #hashtag2 ...
```
