# PhysioSentinel AI v15.5.32

## Cambios exclusivos · Pestaña 10

### 1. Edad/sexo: perfil único por paciente
Problema previo:
la interfaz podía dar la impresión de que había que guardar edad/sexo registro por registro.

Corrección:
- se genera un ID canónico de paciente con `infer_patient_id`;
- aparece un selector `Paciente al que asignar edad y sexo`;
- edad/sexo se guardan UNA sola vez por paciente;
- todos los registros presentes e históricos con ese ID canónico heredan el mismo perfil;
- la interfaz muestra cuántos registros heredarán el perfil;
- al seleccionar un registro se muestra explícitamente qué perfil está aplicado;
- tras guardar se limpian caches y se recalcula la pestaña.

Edad/sexo siguen afectando sólo al plano actual/transversal.

### 2. Coinhibición: compuerta realmente excluyente
En v15.5.31, cuando Coinhibición no cumplía la compuerta fisiológica,
su score se multiplicaba por 0.52. Todavía podía seguir siendo el score más alto.

En v15.5.32:
- si `Coinhibicion_permitida == False`, Coinhibición queda excluida de la competición;
- se conserva `Score_Coinhibicion_bruto` únicamente para auditoría;
- sólo puede ganar si cumple simultáneamente los criterios fisiológicos de V/S/R/C
  reducidos y ausencia de actividad multibanda/dominancia contradictoria.

### 3. Transparencia
El análisis avanzado muestra:
- score usado para decidir;
- score bruto de Coinhibición;
- estado de la compuerta;
- motivo de bloqueo.

### Se conserva
- V/S 55% + L/C/R 45%.
- normalización transversal por edad/sexo.
- longitudinal 100% intraindividual.
- integrado 70/30.
- UI accesible.
- resto de pestañas intacto.
