---
description: Configura el instagram-pipeline en esta máquina (API key de OpenAI + guía de estilo + logos). Correr una vez por máquina.
argument-hint: (sin argumentos)
---

Tu tarea: configurar el instagram-pipeline en esta máquina por primera vez.

IMPORTANTE: Usar SIEMPRE rutas bash. En Windows con Git Bash, el home es `~` (equivale a C:\Users\tu-usuario). NUNCA usar $env:USERPROFILE, NUNCA usar sintaxis PowerShell.

**Paso 1.** Crear el directorio de configuración:

```bash
mkdir -p ~/.claude/instagram-pipeline
```

**Paso 2.** Verificar si ya existe `~/.claude/instagram-pipeline/.env`:

```bash
ls ~/.claude/instagram-pipeline/.env
```

Si el comando devuelve error (archivo no encontrado): pedirle al usuario su API key de OpenAI y crear el archivo:

```bash
echo 'OPENAI_API_KEY=LA_CLAVE_AQUI' > ~/.claude/instagram-pipeline/.env
```

Si ya existe: preguntar si quiere reemplazarla.

No imprimir la clave después de guardarla.

**Paso 3.** Copiar el style guide si no existe:

```bash
ls ~/.claude/instagram-pipeline/style-guide.md
```

Si no existe, copiarlo:

```bash
cp "${CLAUDE_PLUGIN_ROOT}/assets/style-guide-template.md" ~/.claude/instagram-pipeline/style-guide.md
```

**Paso 4.** Copiar los logos si no existen:

```bash
ls ~/.claude/instagram-pipeline/logo.png
```

Si no existe, copiar ambos:

```bash
cp "${CLAUDE_PLUGIN_ROOT}/assets/logo.png" ~/.claude/instagram-pipeline/logo.png
cp "${CLAUDE_PLUGIN_ROOT}/assets/logo-negro.png" ~/.claude/instagram-pipeline/logo-negro.png
```

**Paso 4b.** Copiar el archivo de buyer personas si no existe:

```bash
ls ~/.claude/instagram-pipeline/buyer-personas.md
```

Si no existe, copiarlo:

```bash
cp "${CLAUDE_PLUGIN_ROOT}/assets/buyer-personas.md" ~/.claude/instagram-pipeline/buyer-personas.md
```

**Paso 5.** Verificar que todo quedó bien:

```bash
ls ~/.claude/instagram-pipeline/
```

Mostrar al usuario un resumen:

✅ Configuración completa:
- API key guardada en ~/.claude/instagram-pipeline/.env
- Style guide copiado (colores, tipografías y logos de Uk ya preconfigurados)
- Logos disponibles: logo.png y logo-negro.png

⚠️ Falta completar en ~/.claude/instagram-pipeline/style-guide.md:
- Listado de carreras reales
- CTAs estándar y URL de conversión

Mostrar la ruta completa del archivo para que el usuario sepa dónde editarlo.
