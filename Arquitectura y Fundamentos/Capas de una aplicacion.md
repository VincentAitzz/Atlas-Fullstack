## Concepto general

Una aplicacion bien diseñada se organiza en capas.  
Cada capa agrupa responsabilidades relacionadas y se comunica con las capas vecinas.  
El objetivo es lograr sistemas mas mantenibles, modulares y faciles de escalar.

Separar por capas permite:

- Cambiar una parte del sistema sin afectar todo.
    
- Probar componentes de forma aislada.
    
- Reutilizar logica en distintos puntos de la aplicacion.
    

---

## Modelo clasico de tres capas

1. Capa de presentacion
    
2. Capa de logica de negocio
    
3. Capa de datos
    

Este modelo se usa tanto en aplicaciones web como de escritorio y sirve de base para arquitecturas mas avanzadas.

---

## Capa de presentacion

Responsabilidad principal:

- Interaccion con el usuario (interfaz grafica o API de salida).
    

En aplicaciones web:

- Frontend (HTML, CSS, JavaScript, React, Vue, etc.).
    
- Vistas, templates, componentes.
    
- Validaciones basicas de formularios.
    
- Manejo de estados de interfaz.
    

En APIs:

- Endpoints que exponen datos hacia el exterior.
    
- Formato de las respuestas (JSON, XML, etc.).
    

Puntos clave:

- No debe contener logica de negocio compleja.
    
- Solo orquesta llamadas hacia otras capas y muestra resultados.
    

---

## Capa de logica de negocio (servicios o dominio de aplicacion)

Responsabilidad principal:

- Aplicar reglas y procesos del negocio.
    
- Coordinar operaciones entre diferentes fuentes de datos o servicios.
    

Elementos tipicos:

- Servicios (userService, authService).
    
- Casos de uso (use cases).
    
- Validaciones de negocio.
    
- Procesamiento de datos.
    

Ejemplos:

- Calcular precio final con descuentos.
    
- Verificar si un usuario puede realizar cierta accion.
    
- Aplicar reglas segun roles o estados.
    

Puntos clave:

- No debe depender directamente de detalles tecnicos de la base de datos.
    
- Es el nucleo de la aplicacion: lo que la hace diferente a otras.
    

---

## Capa de datos (persistencia)

Responsabilidad principal:

- Acceso y gestion de datos persistentes.
    

Elementos tipicos:

- Repositorios.
    
- Modelos de base de datos (ORM).
    
- Consultas SQL o drivers NoSQL.
    

Ejemplos:

- UserRepository con metodos como findById, create, update.
    
- Modelos de ORM (Sequelize, Prisma, SQLAlchemy, Django ORM).
    

Puntos clave:

- No debe contener logica de negocio.
    
- Solo se encarga de “como” se obtienen o guardan los datos.
    

---

## Capas extendidas en arquitecturas modernas

Ademas del modelo basico, muchas arquitecturas agregan capas intermedias para mayor control.

Ejemplos comunes:

1. Capa de dominio
    
    - Entidades del negocio (User, Order, Product).
        
    - Reglas invariantes (restricciones fuertes del dominio).
        
2. Capa de aplicacion
    
    - Casos de uso de aplicacion concreta (CreateUser, LoginUser).
        
    - Orquesta llamadas a repositorios y servicios externos.
        
3. Capa de infraestructura
    
    - Implementaciones tecnicas concretas:
        
        - Base de datos especifica.
            
        - Drivers de mensajeria.
            
        - Integraciones con APIs externas.
            

Relacion con Clean Architecture:

- Entities → Capa de dominio.
    
- Use Cases → Capa de aplicacion.
    
- Interface Adapters → Controladores, mapeadores, repositorios.
    
- Frameworks & Drivers → Capa de infraestructura, bases de datos, web.
    

---

## Mapeo entre capas y estructura de carpetas

Ejemplo generico de backend:

/project  
├─ /presentation  
│ ├─ /controllers  
│ └─ /routes  
├─ /application  
│ ├─ /services  
│ └─ /use_cases  
├─ /domain  
│ ├─ /entities  
│ └─ /value_objects  
├─ /infrastructure  
│ ├─ /repositories  
│ ├─ /database  
│ └─ /adapters  
└─ main.(js, ts, py)

Ejemplo simplificado (MVC clasico):

/project  
├─ /models  
├─ /views  
└─ /controllers

---

## Relacion con el frontend

En el frontend tambien se aplican capas:

- Capa de presentacion:
    
    - Componentes visuales, vistas, estilos.
        
- Capa de logica de presentacion:
    
    - Manejo de estado global (Redux, Vuex, Zustand, etc.).
        
    - Servicios de llamadas a APIs (apiClient, httpService).
        
- Capa de modelo o dominio:
    
    - Transformacion y adaptacion de datos recibidos de la API.
        

Recomendacion:

- Evitar meter logica de negocio compleja en los componentes.
    
- Delegar llamadas a API a servicios dedicados.
    

---

## Beneficios de usar capas

1. Mantenibilidad
    
    - Cada cambio se limita a una zona concreta.
        
2. Reutilizacion
    
    - La logica de negocio puede ser usada por distintos clientes (web, mobile, API).
        
3. Testeabilidad
    
    - Es mas facil probar una capa en aislamiento.
        
4. Escalabilidad
    
    - Se pueden reemplazar implementaciones (base de datos, cliente HTTP, etc.) sin cambiar todo.
        

---

## Recomendaciones practicas

- Definir desde el inicio cuantas capas usara el proyecto.
    
- Evitar mezclar logica de negocio en controladores o modelos de base de datos.
    
- Mantener clara la direccion de dependencias:
    
    - Capas superiores dependen de capas inferiores por abstraccion, no al reves.
        
- Documentar la arquitectura de capas en el README o en un diagrama.
    
- Revisar periodicamente que el codigo respete esta separacion.
    

Relacion con otras notas:

- [[Patrones de Software]]
    
- [[Principios SOLID]]
    
- [[Arquitectura de Aplicaciones Web Modernas]]
    
- [[Buenas Practicas Codigo]]