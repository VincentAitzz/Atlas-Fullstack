## Concepto general

En una aplicacion bien estructurada, la logica se divide entre:

- Controladores: reciben y responden peticiones.
    
- Servicios: contienen la logica de negocio.
    
- Repositorios (opcional, pero recomendable): gestionan el acceso a datos.
    

El objetivo es evitar que los controladores se llenen de logica y que los modelos o repositorios decidan reglas de negocio.

---

## Rol de los controladores

Responsabilidad principal:

- Recibir la peticion (HTTP, por ejemplo).
    
- Validar datos básicos de entrada.
    
- Llamar al servicio correspondiente.
    
- Transformar la respuesta del servicio en una respuesta HTTP adecuada.
    

Lo que NO deberían hacer:

- Implementar logica de negocio compleja.
    
- Acceder directamente a la base de datos.
    
- Procesar reglas de autorización complicadas (deberían delegarlas).
    

Puntos clave:

- Son la “entrada” de la aplicacion.
    
- Se centran en protocolo y transporte (HTTP, rutas, parámetros).
    

---

## Rol de los servicios

Responsabilidad principal:

- Contener la logica de negocio de la aplicacion.
    

Ejemplos de tareas tipicas:

- Calculo de precios o impuestos.
    
- Validacion de reglas segun roles.
    
- Procesamiento de datos provenientes de varios repositorios.
    
- Coordinacion de llamadas a otros servicios externos.
    

Puntos clave:

- No dependen de detalles de la capa de transporte (HTTP, Express, etc.).
    
- Se enfocan en el “que hace” la aplicacion, no en “como se expone”.
    

---

## Rol de los repositorios

Responsabilidad principal:

- Gestionar el acceso a los datos (BD u otras fuentes).
    

Ejemplos:

- UserRepository, ProductRepository, OrderRepository.
    
- Metodos tipicos: findById, findAll, create, update, delete.
    

Puntos clave:

- Los servicios llaman a los repositorios.
    
- Los controladores no deberian hablar directamente con la base de datos.
    
- Facilitan cambiar la tecnologia de persistencia sin reescribir la logica de negocio.
    

---

## Flujo tipico de una peticion

1. El cliente envia una peticion HTTP (ejemplo: POST /users).
    
2. El controlador correspondiente recibe la peticion.
    
3. El controlador valida datos basicos y llama al servicio (UserService).
    
4. El servicio aplica reglas de negocio y llama al repositorio (UserRepository).
    
5. El repositorio ejecuta la operacion en la base de datos.
    
6. El servicio procesa el resultado y lo devuelve al controlador.
    
7. El controlador convierte esa informacion en una respuesta HTTP (JSON, codigo de estado adecuado).
    

Direccion general de dependencias:  
Controlador → Servicio → Repositorio → Base de datos

---

## Ejemplo generico de estructura de carpetas

Estructura basada en controladores, servicios y repositorios:

/project  
├─ /src  
│ ├─ /controllers  
│ │ └─ userController.(js, ts, py)  
│ ├─ /services  
│ │ └─ userService.(js, ts, py)  
│ ├─ /repositories  
│ │ └─ userRepository.(js, ts, py)  
│ ├─ /models  
│ │ └─ userModel.(js, ts, py)  
│ └─ app.(js, ts, py)  
└─ package.json

Ejemplo adaptado a un estilo Clean Architecture simplificado:

/project  
├─ /presentation  
│ └─ /controllers  
├─ /application  
│ └─ /services  
├─ /infrastructure  
│ └─ /repositories  
└─ /domain  
└─ /entities

---

## Uso de DTOs (Data Transfer Objects)

Un DTO es un objeto usado para transportar datos entre capas.

Usos tipicos:

- Normalizar datos de entrada (request → DTO).
    
- Controlar que informacion se expone en las respuestas.
    
- Evitar filtrar campos internos o sensibles.
    

Ejemplo conceptual:

- UserCreateDTO: datos necesarios para crear un usuario.
    
- UserResponseDTO: datos permitidos para mostrar al cliente.
    

Beneficios:

- Mayor control sobre lo que entra y lo que sale.
    
- Independencia entre modelos internos y respuestas externas.
    

---

## Reglas practicas para controladores

Buenas practicas:

- Cada metodo del controlador debe ser corto y directo.
    
- Deberia ser posible leer un controlador como “flujo de historia”:
    
    - recibir datos → validar → llamar servicio → responder.
        
- Manejar codigos HTTP y mensajes claros.
    

Evitar:

- Logica de negocio dentro del controlador.
    
- Consultas directas a la base de datos.
    

---

## Reglas practicas para servicios

Buenas practicas:

- Que contengan logica de negocio reutilizable.
    
- No depender directamente de detalles de framework o transporte.
    
- Aplicar principios SOLID (especialmente SRP y OCP).
    

Evitar:

- Convertir el servicio en una clase “Dios” que haga todo.
    
- Mezclar demasiados casos de uso en una sola clase o modulo.
    

---

## Relacion con [[Principios SOLID]]

- SRP:
    
    - Controladores, servicios y repositorios tienen responsabilidades claras y unicas.
        
- OCP:
    
    - Se pueden agregar nuevas funcionalidades creando nuevos servicios o metodos sin modificar los existentes.
        
- DIP (Dependency Inversion):
    
    - Los servicios deberian depender de abstracciones de repositorios, no de implementaciones concretas.
        

Esto facilita pruebas unitarias y cambios futuros.

---

## Beneficios de esta arquitectura

1. Mantenibilidad
    
    - El codigo se organiza por responsabilidades claras.
        
2. Testeabilidad
    
    - Los servicios pueden probarse sin necesidad de levantar el servidor.
        
3. Reutilizacion
    
    - La logica de negocio puede ser usada por distintos tipos de interfaces (REST, CLI, tareas en background).
        
4. Escalabilidad
    
    - Es mas facil dividir un monolito modular en microservicios si la logica ya esta bien separada.
        

---

## Recomendaciones finales

- Definir siempre desde el inicio donde estararan los controladores, servicios y repositorios.
    
- Mantener los controladores lo mas delgados posibles.
    
- Concentrar reglas de negocio en servicios y casos de uso.
    
- Proteger la logica de negocio de detalles tecnicos (HTTP, BD, framework).
    
- Documentar la relacion entre controladores, servicios y repositorios en el README o en diagramas de arquitectura.
    

Relacion con otras notas:

- [[Capas de una aplicacion]]
    
- [[Patrones de Software]]
    
- [[Principios SOLID]]
    
- [[Arquitectura de Aplicaciones Web Modernas]]
    
- [[Buenas Practicas Codigo]]