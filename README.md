# Dashboard F1 - API Jolpica

Dashboard interactivo para visualización de datos de Fórmula 1 usando Node-RED y la API jolpica-f1.

## Autor
Ré, Lautaro Caupolicán

## Descripción
Aplicación web que consume la API pública jolpica-f1 para mostrar:
- Clasificación de pilotos (top 10)
- Clasificación de constructores (gráfico top 5)
- Calendario de carreras de la temporada
- Información de la próxima carrera

## Funcionalidades
- Selector de temporada (1950-presente)
- Actualización manual de datos
- Sistema de caché (5 minutos)
- Manejo centralizado de errores
- Interfaz responsive

## Variables de Entorno
Configuradas en `settings.js` bajo `functionGlobalContext`:

- `API_BASE_URL`: https://api.jolpi.ca/ergast/f1
- `CURRENT_SEASON`: 2025
- `REQUEST_LIMIT`: 30
- `CACHE_DURATION`: 300000 (5 minutos)

## Dependencias
- node-red-dashboard: UI del dashboard
- node-red-contrib-moment: Manejo de fechas

## Instalación
1. Clonar repositorio
2. Abrir Node-RED
3. Importar proyecto desde Projects
4. Instalar dependencias desde Manage Palette
5. Acceder al dashboard en http://localhost:1880/ui

## Estructura
- **[MAIN]**: Interfaz principal y lógica de presentación
- **[API]**: Subflujos para consumo de API (modularizados)
- **[CACHE]**: Sistema de caché temporal
- **[ERROR]**: Manejo centralizado de errores con Catch nodes

## API Utilizada
jolpica-f1 (https://api.jolpi.ca)
- Endpoints: /driverstandings, /constructorstandings, /races
- Documentación: https://github.com/jolpica/jolpica-f1

## Manejo de Errores
- Nodos Catch en cada flujo crítico
- Centralización de errores en pestaña [ERROR]
- Notificaciones al usuario vía UI
- Log persistente en flow context

## Notas
- Los datos se cachean por 5 minutos para reducir requests
- Rate limit de API: 4 req/s, 500 req/hora
- Dashboard optimizado para 1920x1080