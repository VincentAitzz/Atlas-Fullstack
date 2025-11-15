## Concepto general

Una API (Application Programming Interface) define la forma en que diferentes componentes o sistemas se comunican entre sí.  
En desarrollo web moderno, una API suele exponer recursos y operaciones a través de HTTP, normalmente usando JSON.

Un buen diseño de API busca:

- Claridad.
    
- Consistencia.
    
- Previsibilidad.
    
- Facilidad de uso y mantenimiento.
    

---

## Estilo REST (enfoque principal)

La mayoria de APIs modernas siguen el estilo REST o una variante muy cercana.

Principios basicos:

- Recursos identificados por URLs.
    
- Uso coherente de metodos HTTP.
    
- Respuestas autocontenidas (estado, datos y metadatos).
    
- Sin estado en el servidor entre peticiones (stateless).
    

Ejemplos de recursos:

- /users
    
- /products
    
- /orders
    

---

## Rutas y recursos

Reglas generales:

- Usar sustantivos en plural para recursos:
    
    - Correcto: /users, /products
        
    - Evitar: /getUsers, /doLoginUser
        
- Usar rutas jerarquicas para relaciones:
    
    - /users/{id}/orders
        
    - /projects/{id}/tasks
        
- Evitar verbos en las rutas. El verbo lo aporta el metodo HTTP.
    

Ejemplos:

- GET /users → lista de usuarios.
    
- POST /users → crear nuevo usuario.
    
- GET /users/{id} → detalle de un usuario.
    
- PUT /users/{id} → actualizar usuario completo.
    
- PATCH /users/{id} → actualizar parcialmente.
    
- DELETE /users/{id} → eliminar usuario.
    

---

## Metodos HTTP y su uso

Metodos principales:

- GET: obtener recursos, no modifica estado.
    
- POST: crear recursos nuevos.
    
- PUT: reemplazar un recurso completo.
    
- PATCH: actualizar parcialmente un recurso.
    
- DELETE: eliminar un recurso.
    

Propiedades importantes:

- GET y DELETE son normalmente idempotentes (mismo resultado si se repiten).
    
- PUT debe ser idempotente.
    
- POST no es idempotente (cada llamada puede crear algo nuevo).
    

---

## Codigos de estado HTTP

Codigos mas comunes:

- 200 OK
    
    - Respuesta correcta general.
        
- 201 Created
    
    - Recurso creado correctamente (usado con POST).
        
- 204 No Content
    
    - Operacion exitosa sin contenido en respuesta (ejemplo: DELETE).
        
- 400 Bad Request
    
    - Error en los datos enviados por el cliente.
        
- 401 Unauthorized
    
    - Falta autenticacion o token invalido.
        
- 403 Forbidden
    
    - Autenticado, pero sin permisos.
        
- 404 Not Found
    
    - Recurso no encontrado.
        
- 409 Conflict
    
    - Conflicto de estado (recurso ya existe, condicion de version, etc.).
        
- 422 Unprocessable Entity
    
    - Datos recibidos validos en formato pero invalidos en contenido.
        
- 500 Internal Server Error
    
    - Error inesperado en el servidor.
        

Buena practica:

- Usar codigos correctos en lugar de responder siempre 200 o 500.
    

---

## Estructura de peticiones y respuestas

Estructura tipica de solicitud:

- Endpoint (URL).
    
- Metodo HTTP.
    
- Headers (autenticacion, content-type, etc.).
    
- Cuerpo (body) en formato JSON para POST, PUT, PATCH.
    

Ejemplo de cuerpo JSON:  
{  
"name": "Example",  
"email": "example@mail.com"  
}

Estructura tipica de respuesta:

- Codigo de estado HTTP.
    
- Cuerpo con datos en JSON.
    
- Opcionalmente metadatos (paginacion, enlaces, etc.).
    

Ejemplo de respuesta:  
{  
"id": 1,  
"name": "Example",  
"email": "example@mail.com",  
"createdAt": "2025-01-01T10:00:00Z"  
}

---

## Paginacion, filtros y orden

Paginacion tipica:

- Parámetros de consulta (query params):
    
    - ?page=1&pageSize=20
        
    - ?limit=10&offset=20
        

Filtros:

- ?status=active
    
- ?role=admin
    

Orden:

- ?sort=createdAt
    
- ?sort=-createdAt (para descendente, segun definicion).
    

Recomendaciones:

- Mantener convenciones claras en todos los endpoints.
    
- Documentar la forma de usar paginacion y filtros.
    

---

## Versionado de APIs

Motivo:

- Permitir cambios sin romper clientes existentes.
    

Formas comunes:

- Version en la URL:
    
    - /api/v1/users
        
    - /api/v2/users
        
- Version en header (mas avanzado pero menos usado en proyectos simples).
    

Recomendacion:

- Usar version en URL en proyectos normales (mas sencillo y explicito).
    

---

## Manejo de errores

Un buen diseño de API incluye respuestas de error claras y estructuradas.

Ejemplo de formato de error:  
{  
"error": {  
"code": "VALIDATION_ERROR",  
"message": "Los datos enviados no son validos.",  
"details": {  
"email": "Formato invalido",  
"password": "Longitud minima 8"  
}  
}  
}

Buenas practicas:

- Evitar mensajes de error ambiguos.
    
- No exponer detalles internos (trazas, consultas SQL, rutas internas).
    
- Usar un formato de error consistente en toda la API.
    

---

## Autenticacion y autorizacion en APIs

Mecanismos comunes:

- Tokens JWT (Bearer tokens).
    
- Cookies de sesion (especialmente en aplicaciones web tradicionales).
    
- OAuth2 para integraciones de terceros.
    

Puntos clave:

- Endpoints protegidos deben requerir token o sesion.
    
- El servidor debe validar el token y extraer el usuario asociado.
    
- La autorizacion (roles, permisos) se maneja normalmente en la capa de servicios.
    

Ejemplo de header de autenticacion:  
Authorization: Bearer <token_jwt>

---

## Buenas practicas de diseño REST

1. Nombrar recursos de forma clara y coherente.
    
2. Usar metodos HTTP de acuerdo a su semantica.
    
3. No mezclar responsabilidades en un mismo endpoint (por ejemplo, evitar endpoints que cambian multiples recursos sin necesidad).
    
4. Retornar siempre respuestas consistentes (mismo formato para exito y error).
    
5. Evitar acoplar el frontend a detalles internos de la base de datos.
    
6. Limitar la informacion sensible en las respuestas.
    

---

## APIs y seguridad

Aspectos minimos a considerar:

- Validacion y sanitizacion de entradas.
    
- Limites de peticiones (rate limiting).
    
- CORS correctamente configurado.
    
- Manejo correcto de tokens y sesiones.
    
- No exponer endpoints administrativos sin proteccion.
    

Relacion con pentesting:

- Muchos ataques se centran en endpoints mal diseñados.
    
- El diseño debe prever casos limite, abuso de parametros, inyecciones y exposicion de datos.
    

---

## Relacion con otras notas

- [[Arquitectura de Aplicaciones Web Modernas]]
    
- [[Capas de una aplicacion]]
    
- [[Arquitectura de controladores y servicios]]
    
- [[Buenas Practicas Codigo]]
    
- [[Seguridad y Pentesting]]
    

---

## Recomendaciones finales

- Definir un estilo de diseño de API antes de empezar a programar.
    
- Mantener documentacion actualizada de endpoints, parametros y respuestas.
    
- Tratar la API como un contrato: los cambios deben ser controlados.
    
- Pensar siempre la API como producto, no solo como detalle tecnico.