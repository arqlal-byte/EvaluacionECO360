# Monitor ECO — prototipo de monitoreo V1.1

Estado: **en preparación, NO conectado al backend**. La interfaz pública conserva datos demostrativos mientras `config.js` no contenga un endpoint.

## Componentes
- `index.html`: diseño aprobado, núcleo animado, tarjetas, gráficas, fuentes y avisos.
- `monitor-live.js`: módulo de lectura de métricas agregadas y controles de caducidad. No escribe en aplicaciones, Sheets ni Drive.
- `config.js`: única configuración pública del visor. URL de /exec solamente. Prohibido colocar credenciales o IDs privados.
- `Monitor_ECO_Code.gs.txt`: código **privado** que debe instalarse en un proyecto Apps Script nuevo; se entrega por separado, nunca se sube a este GitHub público.

## Instalación pendiente (requiere actuación del propietario)
1. Crear un proyecto independiente de Apps Script llamado **Monitor ECO**.
2. Pegar íntegramente el archivo privado `Monitor_ECO_Code.gs.txt` como `Code.gs`.
3. Ejecutar `verificarECO_Ahora`, revisar permisos y confirmar que pudo abrir los siete Sheets. Debe hacerlo una cuenta autorizada para leer las fuentes.
4. Ejecutar **una sola vez** `instalarMonitorECO`: agrega un disparador de 5 minutos si no existe.
5. Publicar como aplicación web que se ejecuta con la cuenta responsable. **Si se elige acceso 'Cualquiera', el resultado agregado es público**: confirmar que el JSON contiene solo metadatos no personales.
6. Registrar la URL real de despliegue `/exec` en `config.js` como `window.ECO_MONITOR_ENDPOINT = 'https://script.google.com/macros/s/.../exec';`.
7. Confirmar en navegador el cambio de "MODO DEMOSTRACIÓN" a "DATOS REALES DE SHEETS", y que las **seis apps siguen sin prueba funcional**.
8. Validar los registros periódicos, las advertencias por datos desactualizados y la visualización móvil.
9. Documentar la aplicación nueva y sus respaldos en el expediente ECO únicamente cuando se confirme que funciona.

## Alcance verificable del backend
- 7 libros de Sheets: acceso, título esperado y presencia de pestañas designadas.
- Lecturas programadas cada ~5 minutos por activador Apps Script, sujeto a cuotas, autorización y disponibilidad de Google.
- Metadatos agregados en PropertiesService; sin registros de personas, respuestas ni valores de celda.
- No hay pruebas funcionales de las apps, diagnósticos IA reales, corrección automática, comprobación de respaldos o logs operativos.
- Las referencias de dependencia de apps con Sheets son **documentales** y requieren cotejo contra código vigente.
- Gris = no verificado; amarillo/rojo = lectura de Sheets con alerta/error; verde = comprobación de fuente correcta, nunca certificación integral de app.
- Un historial limitado de 85 comprobaciones queda en ScriptProperties. No se creó un Sheet de bitácora ni se editó ninguno existente.

## Seguridad
El tablero en GitHub Pages es público. El endpoint JSONP retorna solo estados y tiempos de metadatos; no debe usarse para datos personales, secretos, nombres de personas ni operaciones administrativas. Los IDs de fuentes solo aparecen en el archivo privado Code.gs. Para incorporar mantenimiento y aprobaciones, diseñar un módulo administrativo autenticado separado del tablero público.

## Recuperación
Respaldo previo a los cambios de integración: rama
`respaldo-monitor-eco-diseno-aprobado-2026-11-06`.
Los archivos del cuestionario Evaluación 360 y su base permanecen fuera de este alcance.
