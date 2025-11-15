## Concepto general

El Ciclo de Vida del Software (SDLC) es un modelo que organiza las fases necesarias para planificar, diseñar, construir, probar, desplegar y mantener un sistema.  
Su uso permite asegurar calidad, reducir riesgos y mantener un proceso estable y predecible durante el desarrollo.

En metodologías modernas (ágiles), el SDLC no es lineal: se repite de forma continua en ciclos cortos.

---

## Fases principales

### 1. Requisitos

Objetivo: definir qué debe hacer el sistema.

Actividades:

- Recolectar necesidades de usuarios o negocio.
    
- Definir objetivos, límites y alcance.
    
- Identificar requerimientos funcionales y no funcionales.
    

Entregables:

- Documento de requisitos.
    
- Historias de usuario.
    
- Casos de uso.
    

Riesgos comunes:

- Requisitos ambiguos o contradictorios.
    
- Alcance mal definido.
    

Checklist:

- ¿Está claro qué problema resuelve el sistema?
    
- ¿Los requisitos están priorizados?
    

---

### 2. Análisis y diseño

Objetivo: definir cómo funcionará el sistema.

Actividades:

- Diseñar la arquitectura general del software.
    
- Diseñar base de datos (ERD, modelos).
    
- Seleccionar lenguajes, frameworks y patrones (MVC, MVT, MVVM, Clean Architecture).
    

Entregables:

- Diagramas UML.
    
- Estructura inicial del proyecto.
    
- Modelo de datos.
    

Riesgos comunes:

- Selección incorrecta de herramientas.
    
- Arquitectura poco escalable.
    

Checklist:

- ¿Existe un documento con la arquitectura acordada?
    
- ¿La estructura del proyecto está definida?
    

---

### 3. Implementación

Objetivo: construir el sistema.

Actividades:

- Programar módulos y componentes.
    
- Usar control de versiones (Git).
    
- Integrar APIs, bases de datos y servicios externos.
    

Entregables:

- Código funcional.
    
- Repositorio limpio.
    
- Scripts de inicialización.
    

Riesgos comunes:

- Inconsistencias en estilos de código.
    
- Falta de modularidad.
    

Checklist:

- ¿El código respeta el diseño previo?
    
- ¿Hay ramas por feature y commits claros?
    

---

### 4. Pruebas

Objetivo: validar que el sistema funciona correctamente.

Actividades:

- Pruebas unitarias.
    
- Pruebas de integración.
    
- Pruebas funcionales.
    
- Pruebas de aceptación.
    

Entregables:

- Reportes de pruebas.
    
- Registro de errores corregidos.
    

Riesgos comunes:

- No probar casos límite.
    
- Pruebas incompletas o desactualizadas.
    

Checklist:

- ¿Cada módulo tiene pruebas mínimas?
    
- ¿Los errores están documentados y corregidos?
    

---

### 5. Despliegue

Objetivo: entregar el sistema al entorno final.

Actividades:

- Montar servidores, contenedores o servicios cloud.
    
- Configurar bases de datos remotas.
    
- Crear una guía de instalación.
    

Entregables:

- Versiones publicadas.
    
- Entorno productivo operativo.
    

Riesgos comunes:

- Conflictos en versiones.
    
- Mala configuración del entorno.
    

Checklist:

- ¿Se documentó el proceso de despliegue?
    
- ¿El entorno reproduce el de desarrollo?
    

---

### 6. Mantenimiento

Objetivo: corregir errores y mejorar el sistema.

Actividades:

- Actualizar dependencias.
    
- Optimizar rendimiento y seguridad.
    
- Agregar mejoras solicitadas.
    

Entregables:

- Historial de cambios.
    
- Parches y fixes.
    
- Nuevas versiones.
    

Riesgos comunes:

- Tecnologías obsoletas.
    
- Falta de control de versiones.
    

Checklist:

- ¿Se registran los cambios?
    
- ¿Las dependencias están actualizadas?
    

---

## Modelos comunes de desarrollo

|Modelo|Características|Ventajas|Desventajas|
|---|---|---|---|
|Cascada|Secuencial; requiere completar una fase antes de pasar a la siguiente.|Sencillo, predecible.|Muy rígido, poco adaptable.|
|Iterativo|Construcción por versiones sucesivas del sistema.|Permite retroalimentación constante.|Puede generar deuda técnica.|
|Ágil|Trabajo en ciclos cortos; prioriza adaptación y entrega rápida.|Enfoque progresivo y flexible.|Requiere coordinación y disciplina.|
|Espiral|Enfoque basado en análisis de riesgos.|Control de riesgo continuo.|Costoso y complejo.|
|DevOps|Desarrollo + operaciones con automatización.|Entregas constantes, CI/CD.|Alta dependencia tecnológica.|

---

## Relación con la arquitectura

- La arquitectura del proyecto (MVC, MVVM, MVT, Clean Architecture) se define durante el análisis y diseño.
    
- La implementación debe respetar la estructura definida.
    
- Una buena arquitectura reduce errores en pruebas y mantenimiento.
    

Referencia: [[Patrones de Software]]

---

## Recomendaciones

- Documentar cada fase con entregables claros.
    
- Usar control de versiones desde el inicio.
    
- Mantener un flujo practico: análisis → desarrollo → pruebas → despliegue.
    
- Revisar periódicamente el proceso para integrar mejoras.
    
- Conectar este documento con notas de metodologías: Scrum, Kanban, DevOps.