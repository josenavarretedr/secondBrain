---
name: ficha-registro
description: 'Ficha de Registro Automático'
user-invocable: true
---

﻿---
name: ficha_registro
description: Ficha de Registro Automático
---

# INSTRUCCIÓN DE AGENTE

## Cuándo usarlo

Para registrar cualquier archivo, recurso o referencia que entra al sistema.

## Prompt

@workspace
Necesito registrar este elemento en el sistema:

Tipo: [archivo / contacto / recurso / referencia / herramienta]
Nombre: [nombre descriptivo]
Proyecto: [PROYECTO o GENERAL]
Descripción: [qué es en 2 líneas]
Ubicación: [Drive link / ruta local / URL]
Origen: [cómo llegó — reunión / descarga / generado / recibido]
Fecha: [hoy]

PASO 1 — Determina dónde registrar según tipo:

- Archivo de proyecto → recursos_drive.md del proyecto
- Contacto → 01_PROYECTOS/[PROYECTO]/stakeholders/ o personas/
- Herramienta → 04_RECURSOS/referencias/herramientas.md
- Referencia académica → 03_NOTEBOOK_LM/links_activos.md
- Recurso general → 04_RECURSOS/referencias/general.md

PASO 2 — Crea o actualiza la ficha con:
| Campo | Valor |
|-------|-------|
| Nombre | |
| Tipo | |
| Proyecto | |
| Descripción | |
| Ubicación | |
| Fecha registro | |
| Origen | |
| Útil para | |

PASO 3 — Si es contacto nuevo → propón agregar a contexto.md del proyecto
PASO 4 — Confirma archivo modificado.


