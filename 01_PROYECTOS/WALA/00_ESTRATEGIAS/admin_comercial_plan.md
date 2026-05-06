# Plan: Admin Comercial Unificado

## Estado: LISTO PARA EJECUTAR

---

## Diagnóstico del código actual

| Problema | Archivos afectados |
|---|---|
| `useComercial.js` no existe → el store importa un composable inexistente | `commerceStore.js` |
| El store carga datos via `loadGlobalCommerceData(excludedEmails)` (multi-tenant con exclusiones por email) | `commerceStore.js`, `AdminCommercialDashboard.vue` |
| Rutas Firestore apuntan a `businesses/{id}/leads`, `businesses/{id}/visitas`, etc. | `commerceStore.js` (referenciado) |
| `QuickEntryModal` recibe prop `businesses` y emite `leadId` para resolución externa | `QuickEntryModal.vue`, `AdminCommercialDashboard.vue` |
| `PipelineLeads` emite `businessId` en update-status | `PipelineLeads.vue` |
| `CommercialKPIs` — estructura props compatible, solo necesita que KPIs vengan de `records` | `CommercialKPIs.vue` |
| Sin regla Firestore explícita para colección `comercial` (actualmente pasa por allow all) | `firestore.rules` |
| Sin índices para colección `comercial` | `firestore.indexes.json` |

---

## Contrato de datos (Fase 1)

### `comercial/settings` — docType: 'settings'
```js
{
  docType: 'settings',
  activeZones: string[],
  activeSectors: string[],
  metasSemanales: {
    visitasTarget: number,
    agendadosTarget: number,
    tasaAgendamientoMin: number,
    cierresTarget: number,
    tasaCierreMin: number,
    cajaTarget: number
  },
  whatsappTemplates: {
    pitch: string,
    seguimiento48h: string,
    cierre: string,
    confirmacionWala: string
  },
  campanas: string[],       // opcional
  cohortes: string[],       // opcional
  updatedAt: Timestamp
}
```

### `comercial/{recordId}` — docType: 'record'
```js
{
  docType: 'record',
  // Obligatorios
  eventType: 'visita' | 'diagnostico' | 'cierre' | 'seguimiento',
  statusPipeline: 'nuevo' | 'diagnosticado' | 'en_seguimiento' | 'cerrado' | 'descartado',
  businessName: string,       // texto libre
  contactName: string,
  contactPhone: string,
  zona: string,
  sector: string,
  resultado: string,
  monto: number,
  fechaEvento: Timestamp,
  notas: string,
  createdAt: Timestamp,
  updatedAt: Timestamp,
  // Opcionales por etapa
  fechaAgendada?: Timestamp,
  tipoCierre?: 'advisory' | 'wala',
  tipoSeguimiento?: 'pre_diagnostico' | 'post_diagnostico' | 'post_cierre',
  areasCriticas?: string[],
  mensajeWhatsapp?: string,
  cohorte?: string,
  campana?: string
}
```

---

## Archivos a crear/modificar

### CREAR: `src/composables/useComercial.js`
Operaciones CRUD solo sobre colección `comercial`:
- `fetchSettings()` → lee `comercial/settings`
- `saveSettings(data)` → escribe `comercial/settings`  
- `fetchRecords(filters?)` → lee `comercial` where `docType == 'record'`
- `createRecord(data)` → agrega doc en `comercial/`
- `updateRecord(recordId, data)` → actualiza `comercial/{recordId}`
- `deleteRecord(recordId)` → elimina `comercial/{recordId}`
- `getKPIsWeekly(records)` → client-side sobre records de la semana actual

### REFACTOR: `src/stores/commerceStore.js`
Estado plano: `settings`, `records`, `filters`, `loading`, `error`  
Sin: `businesses`, `businessId`, `currentBusiness`, exclusiones de email  
Getters: `recordsByStatus`, `filteredRecords`, `kpisWeekly`, `metasSemanales`, `disponibleZones`, `disponibleSectors`

### REFACTOR: `src/views/Admin/AdminCommercialDashboard.vue`
`onMounted` → `fetchSettings() + fetchRecords()` (sin argumento businessId)  
`saveConfig` → `updateSettings()` (sin bucle multi-tenant)  
`handleQuickEntrySubmit` → `createRecord(payload)` directo  
`handleUpdateStatus` → `updateRecord(recordId, {statusPipeline})` sin businessId

### REFACTOR: `src/components/Admin/QuickEntryModal.vue`
Eliminar prop `businesses` y prop `existingLeads`  
El payload emitido mapea directamente al schema de `record`  
`businessName` = texto libre

### REFACTOR: `src/components/Admin/PipelineLeads.vue`
`filteredLeadsByStatus` → opera sobre `statusPipeline` en vez de `status`  
`markDescartado(recordId)` → emite solo `{recordId, statusPipeline: 'descartado'}`, sin `businessId`  
Campos de display: `contactName`, `contactPhone`, `businessName`

### REFACTOR: `src/components/Admin/CommercialKPIs.vue`
Sin cambios estructurales — los props `kpis` y `metas` se mantienen iguales  
Solo se verifica que `alertas` funcione correctamente desde el nuevo cálculo

### UPDATE: `firestore.rules`
Agregar sección `comercial`:
```
match /comercial/{docId} {
  allow read, write: if request.auth != null && isAdmin();
}
```
Donde `isAdmin()` puede ser una función que verifica un claim o email.

### UPDATE: `firestore.indexes.json`
Agregar índices sobre colección `comercial`:
- `docType + statusPipeline + fechaEvento`
- `docType + zona + fechaEvento`
- `docType + cohorte + fechaEvento`

---

## Orden de ejecución

```
Fase 1: Crear useComercial.js (bloquea todo)
    ↓
Fase 2: Refactor commerceStore.js
    ↓
Fase 3+4: Refactor AdminCommercialDashboard.vue
    ↓ (paralelo)
Fase 5: QuickEntryModal.vue     Fase 6: PipelineLeads.vue + CommercialKPIs.vue
    ↓
Fase 7: firestore.rules + firestore.indexes.json
    ↓
Fase 8: Verificación
```

---

## Residuos a eliminar
- `businesses` ref en store
- `fetchGlobalData(excludedEmails)` → reemplazar por `fetchSettings() + fetchRecords()`
- `updateGlobalConfig` (bucle multi-tenant) → reemplazar por `saveSettings()`
- `loadBusinessesCatalog` import
- `businessId` parámetro en todas las acciones del store
- Prop `businesses` en `QuickEntryModal`
- Prop `businessId` en emit de `PipelineLeads`
- Resolución `businessIdFromLead || businessIdFromName` en dashboard

---

> [!IMPORTANT]
> `comercial/settings` es el único documento con `docType: 'settings'`. Todos los demás documentos tienen `docType: 'record'`. La query de records usa `where('docType', '==', 'record')`.
