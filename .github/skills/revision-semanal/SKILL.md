---
name: revision-semanal
description: 'Revisión Semanal'
user-invocable: true
---

﻿---
name: revision_semanal
description: Revisión Semanal
---

# INSTRUCCIÓN DE AGENTE

## Cuándo usarlo

Cada viernes noche o lunes mañana.

## Prompt

@workspace
Es [inicio/fin] de semana. Lee:

- 00_CONTEXTO/estado_actual.md
- Todos los diarios de esta semana en 02_DIARIO/
- to-dos_activos.md de cada proyecto
- contexto.md de cada proyecto

GENERA REPORTE SEMANAL:

## Semana [NÚMERO] — [Fechas]

### ✅ Completado vs Prometido

| Proyecto | Prometido | Completado | %   |
| -------- | --------- | ---------- | --- |

### 💰 Cashflow de la semana

| Fuente | Estado | Monto | Próxima acción |
| ------ | ------ | ----- | -------------- |

### 🧠 Hipótesis

| Hipótesis | Estado                            | Evidencia |
| --------- | --------------------------------- | --------- |
|           | Validada / Descartada / Pendiente |           |

### 📈 Top 3 prioridades semana siguiente

1.
2.
3.

### ⚠️ Frentes a cerrar o pausar

-

PASO FINAL — Genera borrador actualizado de estado_actual.md
para la próxima semana. Muestra diff. Confirma antes de guardar.


