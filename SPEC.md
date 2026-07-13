# SPEC.md

## Visión

Crear una aplicación web mínima para gestionar tareas de un equipo.
Permite crear, listar, completar, eliminar y filtrar tareas desde una
única interfaz.

------------------------------------------------------------------------

# Alcance del MVP

## Entra

-   Crear una tarea con:
    -   Título
    -   Persona asignada
-   Listar todas las tareas.
-   Marcar una tarea como completada.
-   Eliminar una tarea.
-   Filtrar tareas:
    -   Todas
    -   Pendientes
    -   Completadas
-   Backend REST con Node.js + Express.
-   Frontend en un único `index.html` servido por Express.
-   Datos almacenados únicamente en memoria.

## No entra

-   Base de datos.
-   Autenticación o autorización.
-   Edición de tareas.
-   Fechas de creación o vencimiento.
-   Prioridades.
-   Categorías o etiquetas.
-   Comentarios.
-   Persistencia tras reiniciar el servidor.
-   Paginación.
-   Búsqueda.
-   Validaciones complejas.

------------------------------------------------------------------------

# Modelo de datos

## Tarea

  Campo       Tipo      Descripción
  ----------- --------- ---------------------
  id          Number    Identificador único
  title       String    Título de la tarea
  assignee    String    Persona asignada
  completed   Boolean   Estado de la tarea

Ejemplo:

``` json
{
  "id": 1,
  "title": "Preparar demo",
  "assignee": "Ana",
  "completed": false
}
```

------------------------------------------------------------------------

# API REST

  --------------------------------------------------------------------------------------------------------------
  Método             Ruta             Cuerpo                                              Respuesta
  ------------------ ---------------- --------------------------------------------------- ----------------------
  GET                /api/tasks       \-                                                  Array de tareas

  POST               /api/tasks       `{ "title": "Preparar demo", "assignee": "Ana" }`   Tarea creada

  PATCH              /api/tasks/:id   `{ "completed": true }`                             Tarea actualizada

  DELETE             /api/tasks/:id   \-                                                  `204 No Content`
  --------------------------------------------------------------------------------------------------------------

------------------------------------------------------------------------

# Interfaz

La aplicación muestra una única página con:

-   Formulario para crear una tarea.
-   Grupo de filtros.
-   Lista de tareas.
-   Cada tarea muestra título, persona asignada, estado y acciones.

------------------------------------------------------------------------

# Criterios de aceptación

-   Crear tareas.
-   Listar tareas.
-   Marcar como completada.
-   Eliminar tareas.
-   Filtrar por estado.
-   Las tareas se pierden al reiniciar el servidor.

------------------------------------------------------------------------

# Restricciones técnicas

-   Backend: Node.js + Express.
-   JavaScript (sin TypeScript).
-   Sin base de datos.
-   Array en memoria.
-   Frontend HTML, CSS y JavaScript vanilla.
-   Un único `index.html`.
-   Comunicación mediante `fetch`.
