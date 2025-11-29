# Dashboard F1 - API Jolpica

Dashboard interactivo para visualización de datos de Fórmula 1 usando Node-RED y la API jolpica-f1.

## Autor
Ré, Lautaro Caupolicán

## Descripción
Aplicación web que consume la API pública jolpica-f1 para mostrar:
- Clasificación de pilotos (top 10, paginado y con buscador)
- Clasificación de constructores (gráfico top 5, paginado y con buscador)
- Calendario de carreras de la temporada
- Información de la próxima carrera

## Funcionalidades
- Selector de temporada (1950-presente)
- Actualización manual de datos
- Manejo centralizado de errores
- Interfaz responsive

## Variables de Entorno
- `API_BASE_URL`: https://api.jolpi.ca/ergast/f1
- `CURRENT_SEASON`: 2025
- `REQUEST_LIMIT`: 30
- `CACHE_DURATION`: 300000 (5 minutos)

## Dependencias
- @flowfuse/node-red-dashboard: UI del dashboard

## Instalación
1. Clonar repositorio
2. Abrir Node-RED
3. Importar proyecto desde Projects
4. Instalar dependencias desde Manage Palette
5. Acceder al dashboard en http://localhost:1880/dashboard

## Estructura
- **[MAIN]**: Interfaz principal y lógica de presentación
- **[API]**: Subflujos para consumo de API (modularizados)
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
- Dashboard optimizado para 1920x1080
