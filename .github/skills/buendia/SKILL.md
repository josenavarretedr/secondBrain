---
name: buendia
description: 'Inicia el día con prioridades precargadas'
user-invocable: true
---

﻿---
name: buenDia
description: Inicia el día con prioridades precargadas
---

# INSTRUCCIÓN DE AGENTE

## Cuándo usarlo

Cada mañana antes de empezar a trabajar.

## Prompt

@workspace
Actúa como mi asistente de arranque bajo MODO MMOOD.

PASO 1 — Lee estos archivos:

- 00_CONTEXTO/estado_actual.md
- 00_CONTEXTO/arquitectura_sistema.md
- El diario más reciente en 02_DIARIO/
- to-dos_activos.md de CADA proyecto en 01_PROYECTOS/

PASO 2 — Crea la nota del día:

- Nombre: 02_DIARIO/[FECHA_HOY].md
- Usa exactamente la plantilla en 04_RECURSOS/plantillas/diario_template.md
- Precarga en TOP 3 las acciones más urgentes según prioridad:
  1. Cashflow inmediato (💰)
  2. Escalabilidad WALA (📈)
  3. Validación / Otros frentes activos (🏛️ / 🧠 - ej. TFM, o SOMU sólo si requiere acción real y no está en Standby)

PASO 3 — Alerta si existe:

- Algún to-do vencido (fecha límite ya pasó)
- Algún proyecto sin actividad más de 5 días
- Alguna hipótesis sin validar más de 2 semanas

PASO 4 — Dame:

- Tabla con TOP 3 acciones del día
- Lista de alertas activas
- Una sola frase de foco para el día (estilo estoico)

No preguntes. Ejecuta y muestra resultado.

