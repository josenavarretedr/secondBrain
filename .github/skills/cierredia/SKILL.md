---
name: cierredia
description: 'Procesa el diario de hoy y distribuye to-dos'
user-invocable: true
---

﻿---
name: cierreDia
description: Procesa el diario de hoy y distribuye to-dos
---

# INSTRUCCIÓN DE AGENTE

## Cuándo usarlo

Cada noche antes de cerrar VS Code.

## Prompt

@workspace
Actúa como mi agente de cierre bajo MODO MMOOD.

PASO 1 — Lee el diario de hoy:

- 02_DIARIO/[FECHA_HOY].md

PASO 2 — Extrae y distribuye:

- Ideas etiquetadas [WALA] → agregar a 01_PROYECTOS/WALA/to-dos_activos.md
- Ideas etiquetadas [ALDEAS] → agregar a 01_PROYECTOS/ALDEAS_INFANTILES/to-dos_activos.md
- Ideas etiquetadas [TESIS] → agregar a 01_PROYECTOS/TESIS_MAESTRIA/to-dos_activos.md
- Ideas etiquetadas [SOMU] → agregar a 01_PROYECTOS/SOMU/to-dos_activos.md
- Ideas etiquetadas [CONTENIDO] → agregar a 01_PROYECTOS/CONTENIDO_REDES/to-dos_activos.md
- Ideas etiquetadas [IDEA] sin proyecto → agregar a 03_NOTEBOOK_LM/ideas_sueltas.md

PASO 3 — Detecta decisiones:

- ¿Alguna decisión tomada hoy modifica el contexto de un proyecto?
- Si sí → propón actualización de contexto.md del proyecto correspondiente
- Muestra antes/después y espera confirmación

PASO 4 — Actualiza estado_actual.md:

- Marca como completados los to-dos ejecutados hoy
- Agrega nuevos to-dos detectados
- Actualiza fecha de última modificación
- Muestra diff completo antes de guardar

PASO 5 — Resumen ejecutivo del día:
| Métrica | Resultado |
|---------|----------|
| To-dos completados | |
| Ideas capturadas | |
| Decisiones tomadas | |
| ¿Avanzó cashflow? | Sí / No |
| ¿Avanzó SOMU? | Sí / No |
| ¿Avanzó WALA? | Sí / No |

Confirma antes de guardar cambios en archivos existentes.


