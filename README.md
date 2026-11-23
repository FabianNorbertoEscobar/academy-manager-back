# Academy Manager API

API REST de ejemplo para gestionar una academia. El proyecto sirve como backend para una aplicación de gestión de usuarios, cursos y estudiantes.

## Stack y tecnologías

- **Node.js**: entorno de ejecución de JavaScript en el servidor.
- **JavaScript (CommonJS)**: lenguaje y sistema de módulos (`require` / `module.exports`).
- **Express 4**: servidor HTTP y definición de rutas.
- **CORS**: middleware para permitir solicitudes desde otros orígenes.
- **JSON**: formato de entrada y salida de la API.
- **Vercel**: plataforma de despliegue; la configuración está en `vercel.json`.

## Funcionalidades

- Operaciones CRUD para usuarios, cursos y estudiantes.
- Consulta de una colección completa o de un elemento por su identificador.
- Respuestas JSON y códigos HTTP como `201`, `204` y `404`.
- Datos de ejemplo cargados en memoria al iniciar la aplicación.
- Endpoint raíz para consultar los recursos disponibles.

## Conceptos del curso aplicados

Este proyecto pone en práctica conceptos habituales de desarrollo backend:

- Construcción de una API REST y diseño de endpoints con métodos HTTP.
- Creación de un servidor y organización de rutas con Express.
- Uso de middleware para procesar JSON y habilitar CORS.
- Lectura de parámetros de ruta (`:id`) y manejo de respuestas y errores HTTP.
- Operaciones CRUD sobre colecciones de datos.
- Uso de variables de entorno, dependencias de npm y despliegue en la nube.

## Requisitos

- Node.js y npm instalados.

## Ejecución local

```bash
npm install
npm start
```

El servidor escucha en `http://localhost:3000` de forma predeterminada. Se puede cambiar el puerto definiendo la variable de entorno `PORT`.

Para iniciar el servidor en desarrollo también está disponible `npm run dev`.

## API

Todos los recursos usan el prefijo `/api`. La API desplegada está disponible en `https://academy-manager-back.vercel.app`.

| Recurso | Listar | Consultar por ID | Crear | Actualizar | Eliminar |
| --- | --- | --- | --- | --- | --- |
| Usuarios | `GET /api/users` | `GET /api/users/:id` | `POST /api/users` | `PUT /api/users/:id` | `DELETE /api/users/:id` |
| Cursos | `GET /api/courses` | `GET /api/courses/:id` | `POST /api/courses` | `PUT /api/courses/:id` | `DELETE /api/courses/:id` |
| Estudiantes | `GET /api/students` | `GET /api/students/:id` | `POST /api/students` | `PUT /api/students/:id` | `DELETE /api/students/:id` |

El endpoint `GET /` devuelve un mensaje y las rutas principales. Las consultas por un ID inexistente responden `404`; las creaciones responden `201` y las eliminaciones exitosas, `204`.

### Modelos de datos de ejemplo

- **Usuario**: `id`, `username`, `email`, `password`, `role`.
- **Curso**: `id`, `title`, `description`, `beginDate`, `endDate`, `status`.
- **Estudiante**: `id`, `firstName`, `lastName`, `gender`, `birthDate`, `email`, `photoUrl`.

Los valores admitidos de `role`, `status` y `gender` pueden consultarse en los datos de ejemplo de `index.js`.

### Ejemplos

```bash
# Listar cursos
curl https://academy-manager-back.vercel.app/api/courses

# Consultar un estudiante
curl http://localhost:3000/api/students/1

# Crear un curso
curl -X POST http://localhost:3000/api/courses \
  -H "Content-Type: application/json" \
  -d '{
    "id": "11",
    "title": "Guitarra",
    "description": "Introducción al instrumento",
    "beginDate": "2025-09-01",
    "endDate": "2025-12-01",
    "status": "SCHEDULED"
  }'
```

Para actualizar, `PUT` reemplaza el elemento con el cuerpo JSON enviado. Las operaciones de escritura modifican únicamente los datos en memoria del proceso.

## Despliegue en Vercel

Con la CLI de Vercel instalada, ejecuta:

```bash
npm install -g vercel
vercel
```

Para desplegar a producción:

```bash
vercel --prod
```

## Alcance y limitaciones

Este backend está pensado para aprendizaje y demostración: no utiliza una base de datos, por lo que los datos no son persistentes y pueden reiniciarse al detener o volver a desplegar la aplicación. Tampoco implementa autenticación, autorización ni validación de datos. CORS está habilitado para todos los orígenes; antes de usarlo en producción, estas capacidades y la configuración de seguridad deben revisarse.
