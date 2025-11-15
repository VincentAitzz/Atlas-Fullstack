## Concepto general

Las buenas prácticas de código son un conjunto de reglas, estilos y convenciones que permiten escribir software más legible, mantenible, escalable y seguro.  
Aplican sin importar el lenguaje o el framework utilizado.

El objetivo principal es reducir errores, facilitar la colaboración y asegurar la calidad del proyecto.

---

## Organización del código

1. Mantener una estructura clara de carpetas.
    
2. Separar responsabilidades en módulos independientes.
    
3. Evitar archivos excesivamente largos o con múltiples funciones no relacionadas.
    
4. Nombrar archivos según su propósito (userController, authService, databaseConfig).
    

Checklist:

- ¿Cada archivo tiene una única responsabilidad?
    
- ¿Es fácil encontrar dónde está la lógica principal?
    

---

## Convenciones de nombres

1. Usar nombres descriptivos y consistentes.
    
2. Usar camelCase para variables y funciones (según el lenguaje).
    
3. Usar PascalCase para clases o modelos.
    
4. Evitar abreviaciones exageradas o confusas.
    
5. Mantener un estilo homogéneo en todo el proyecto.
    

Ejemplo incorrecto:  
vr u = getU()

Ejemplo correcto:  
const user = getUser()

---

## Funciones y métodos

1. Deben realizar una sola tarea específica (relacionado con SRP).
    
2. Evitar funciones demasiado largas o complejas.
    
3. Preferir funciones puras cuando sea posible.
    
4. Seguir un orden lógico en los parámetros.
    
5. Manejar errores y excepciones dentro de las funciones sensibles.
    

Checklist:

- ¿Es fácil explicar qué hace esta función en una frase?
    
- ¿Tiene más de un propósito o mezcla lógica?
    

---

## Comentarios y documentación

1. Comentar solo cuando sea necesario para aclarar intención.
    
2. Evitar comentarios redundantes que expliquen cosas obvias.
    
3. Documentar decisiones importantes directamente en el código o en el README.
    
4. Mantener actualizado lo que se documenta.
    

Buenas prácticas:

- Un comentario debe explicar el “por qué”, no el “qué”.
    

---

## Manejo de errores

1. Validar entradas y parámetros.
    
2. Utilizar estructuras try/catch cuando corresponda.
    
3. Definir mensajes de error claros y útiles.
    
4. Evitar mostrar errores internos al usuario final.
    
5. Registrar errores críticos en logs.
    

Checklist:

- ¿El usuario recibe un error comprensible?
    
- ¿Los errores relevantes quedan registrados?
    

---

## Formato y estilo

1. Mantener sangría consistente.
    
2. Usar un formateador automático (Prettier, Black, ESLint, etc.).
    
3. Evitar líneas extremadamente largas.
    
4. Separar bloques lógicos con espacios.
    

Beneficios:

- El código se vuelve más fácil de leer.
    
- Evita discusiones innecesarias sobre estilo.
    

---

## Seguridad básica en el código

1. No exponer datos sensibles en el repositorio (tokens, API keys, contraseñas).
    
2. Usar variables de entorno para configuraciones críticas.
    
3. Validar y sanitizar datos recibidos de entradas externas.
    
4. Cifrar contraseñas y manejar tokens correctamente.
    
5. Mantener dependencias actualizadas para evitar vulnerabilidades.
    

Conectar con: [[Seguridad y Pentesting]]

---

## Control de versiones

1. Uso obligatorio de Git en todos los proyectos.
    
2. Commits descriptivos siguiendo una convención (por ejemplo, estilo “feat:”, “fix:”, “refactor:”).
    
3. Crear ramas por feature o problema.
    
4. Evitar commits masivos que mezclen múltiples cambios.
    

Checklist:

- ¿El historial refleja cómo evolucionó el proyecto?
    
- ¿Cada commit tiene un propósito único?
    

---

## Pruebas y calidad

1. Añadir pruebas unitarias para funciones clave.
    
2. Realizar pruebas de integración en servicios importantes.
    
3. Automatizar pruebas cuando sea posible.
    
4. Revisar el código (code review) antes de mezclar ramas.
    

Objetivo:

- Reducir errores en producción y asegurar estabilidad.
    

---

## Recomendaciones finales

- Mantener consistencia en todo el proyecto.
    
- Aplicar principios SOLID como guía de diseño.
    
- Documentar decisiones importantes en el proyecto.
    
- Evitar complejidad innecesaria: el código debe ser claro antes que “inteligente”.
    
- Reescribir partes mal diseñadas antes de que escalen y generen deuda técnica.