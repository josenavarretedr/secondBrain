---
name: generador_pdf
description: Generador de Documento Profesional
---

# INSTRUCCIÓN DE AGENTE

## Cuándo usarlo

Para presentaciones a clientes, instituciones o stakeholders.

## Prompt

@workspace
Necesito generar un documento profesional del proyecto [PROYECTO].
Destinatario: [cliente / institución / interno]
Propósito: [propuesta / informe / presentación / reporte]

PASO 1 — Lee toda la carpeta 01_PROYECTOS/[PROYECTO]/ incluyendo:

- contexto.md
- to-dos_activos.md
- estrategias/
- recursos_drive.md
- reuniones/ (últimas 3)

PASO 2 — Genera documento en markdown con esta estructura:

# [Nombre del Proyecto] — [Tipo de documento]

## Fecha: [hoy]

## Preparado por: NEWCOOP

### 1. Resumen Ejecutivo (desde contexto.md)

### 2. Estado Actual (desde estado_actual.md)

### 3. Plan de Acción (desde to-dos_activos.md)

### 4. Estrategia Vigente (desde estrategias/)

### 5. Próximos Pasos (top 3 acciones)

### 6. Recursos y Referencias (desde recursos_drive.md)

PASO 3 — Guarda como:
04*RECURSOS/reportes/[PROYECTO]*[TIPO]\_[FECHA].md

PASO 4 — Confirma ruta del archivo creado.
Listo para exportar a PDF con cualquier conversor markdown.

