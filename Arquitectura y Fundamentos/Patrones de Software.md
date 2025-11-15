## Concepto general

Un patrón de software define una forma estructurada de organizar el código en un proyecto.  
Su propósito es mantener orden, escalabilidad y separación de responsabilidades entre las distintas partes del sistema.  
No depende del lenguaje ni del framework utilizado.

---

## Principales arquitecturas

### 1. MVC (Model - View - Controller)

Estructura más utilizada en backends.

- Model: gestiona datos, lógica de negocio y acceso a la base de datos.
    
- View: representa la interfaz que muestra información al usuario (HTML, JSON, etc.).
    
- Controller: recibe las peticiones, coordina el flujo entre modelo y vista.
    

Ejemplo de estructura (Express):

/project/  
├─ /models/  
│ └─ userModel.js  
├─ /controllers/  
│ └─ userController.js  
├─ /routes/  
│ └─ userRoutes.js  
└─ app.js

Frameworks comunes: Express, Laravel, Spring MVC.

---

### 2. MVT (Model - View - Template)

Variante del MVC usada principalmente en Django.

- Model: define los datos mediante ORM.
    
- View: procesa solicitudes y envía datos a la plantilla.
    
- Template: archivo HTML que renderiza la información final.
    

Ejemplo de estructura (Django):

/project/  
├─ /app/  
│ ├─ /migrations/  
│ ├─ /templates/  
│ │ └─ index.html  
│ ├─ /static/  
│ ├─ models.py  
│ ├─ views.py  
│ ├─ urls.py  
│ └─ admin.py  
├─ manage.py  
└─ settings.py

Framework: Django.

---

### 3. MVVM (Model - View - ViewModel)

Usado en frameworks frontend modernos.

- Model: datos y lógica.
    
- View: interfaz de usuario.
    
- ViewModel: puente entre modelo y vista, sincroniza cambios automáticamente (data binding).
    

Ejemplo de estructura (Vue):

/project/  
├─ /src/  
│ ├─ /assets/  
│ ├─ /components/  
│ │ └─ UserCard.vue  
│ ├─ /views/  
│ │ └─ HomeView.vue  
│ ├─ /store/  
│ │ └─ index.js  
│ ├─ /router/  
│ │ └─ index.js  
│ ├─ App.vue  
│ └─ main.js  
└─ package.json

Frameworks comunes: Vue, Angular.

---

### 4. Clean Architecture

Propuesta por Robert C. Martin (Uncle Bob).  
Busca independencia entre capas para lograr sistemas mantenibles.

Capas típicas:

- Entities: reglas del negocio.
    
- Use Cases: lógica de aplicación.
    
- Interface Adapters: controladores, repositorios, DTOs.
    
- Frameworks & Drivers: base de datos, UI, APIs externas.
    

Ejemplo de estructura (FastAPI o Node):

/project/  
├─ /core/  
│ ├─ /entities/  
│ └─ /use_cases/  
├─ /infrastructure/  
│ ├─ /database/  
│ ├─ /repositories/  
│ └─ /adapters/  
├─ /interfaces/  
│ ├─ /controllers/  
│ └─ /routers/  
└─ main.py (o app.js)

Frameworks comunes: FastAPI, NestJS.

---

## Comparativa general

|Patrón|Orientado a|Complejidad|Ejemplos|
|---|---|---|---|
|MVC|Aplicaciones backend estructuradas|Media|Express, Laravel|
|MVT|Aplicaciones web con plantillas|Media|Django|
|MVVM|Frontends dinámicos|Alta|Vue, Angular|
|Clean Architecture|Proyectos grandes y mantenibles|Alta|FastAPI, NestJS|

---

## Recomendaciones prácticas

- Usa MVC en proyectos pequeños o medianos.
    
- Adopta Clean Architecture si el proyecto escalará con el tiempo.
    
- Mantén separadas las responsabilidades de cada capa.
    
- Documenta siempre el flujo entre componentes (entrada → lógica → salida).
    
- Relaciona esta nota con: [[Ciclo de Vida del Software (SDLC)]] y [[Principios SOLID]].