---
name: sync
description: 'Sincroniza en caliente el diario de hoy, distribuye to-dos y actualiza el estado operativo sin cerrar el día.'
user-invocable: true
---

# INSTRUCCIÓN DE AGENTE

## Cuándo usarlo
Durante el día, cuando agregas tareas, ideas o decisiones en la nota diaria y quieres distribuirlas e integrarlas al sistema sin dar por terminado el día.

## Prompt
@workspace
Actúa como mi agente de sincronización bajo MODO MMOOD.

PASO 1 — Lee el diario de hoy:
- 02_DIARIO/[FECHA_HOY].md

PASO 2 — Extrae y distribuye (en caliente):
- Ideas/to-dos etiquetados [WALA] → agregar a 01_PROYECTOS/WALA/to-dos_activos.md
- Ideas/to-dos etiquetados [AISOS] → agregar a 01_PROYECTOS/AISOS/to-dos_activos.md
- Ideas/to-dos etiquetados [TESIS] o [TFM] → agregar a 01_PROYECTOS/TFM/to-dos_activos.md
- Ideas/to-dos etiquetados [SOMU] → agregar a 01_PROYECTOS/SOMU/to-dos_activos.md
- Ideas/to-dos etiquetados [CONTENIDO] → agregar a 01_PROYECTOS/CONTENIDO_REDES/to-dos_activos.md
- Ideas/to-dos etiquetados [IDEA] sin proyecto → agregar a 03_NOTEBOOK_LM/ideas_sueltas.md

PASO 3 — Sincroniza estado_actual.md:
- Lee 00_CONTEXTO/estado_actual.md
- Sincroniza los to-dos marcados como completados hoy en el diario.
- Agrega nuevos frentes activos o hitos detectados hoy.
- Muestra el diff antes de guardar.

PASO 4 — Confirmación de Sincronización:
- Presenta un reporte ultra-corto de lo sincronizado.
- Recuerda que la jornada sigue activa.
