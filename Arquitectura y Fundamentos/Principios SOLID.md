## Concepto general

Los principios SOLID son un conjunto de cinco reglas destinadas a mejorar la estructura, mantenibilidad y escalabilidad del código en sistemas orientados a objetos.  
Estos principios ayudan a evitar código rígido, difícil de modificar, poco reutilizable o propenso a errores.
 
Se utilizan en prácticamente cualquier backend moderno: Node.js (con clases), Python, Java, C#, etc.

---

## 1. Single Responsibility Principle (SRP)

Cada clase, módulo o componente debe tener **una única responsabilidad**.  
Debe existir **una sola razón para que cambie**.

Problemas evitados:

- Clases demasiado grandes.
    
- Modificaciones riesgosas porque afectan múltiples funcionalidades.
    

Ejemplo conceptual:  
Una clase que maneja usuarios no debe encargarse también de enviar correos, registrar logs ni validar tokens.

---

## 2. Open / Closed Principle (OCP)

Los módulos deben estar **abiertos a extensión** pero **cerrados a modificación**.  
Se debe poder agregar nueva funcionalidad sin alterar el código existente.

Aplicación común:

- Uso de interfaces.
    
- Uso de herencia o composición.
    
- Uso de inyección de dependencias.
    

Evita:

- Romper funciones existentes al agregar nuevas variantes.
    
- Mezclar múltiples comportamientos dentro del mismo bloque de código.
    

---

## 3. Liskov Substitution Principle (LSP)

Las clases hijas deben poder reemplazar a la clase padre **sin alterar el comportamiento del programa**.

Indica que la herencia debe aplicarse solo cuando exista una verdadera relación padre-hijo.

Se viola cuando:

- Una clase hija lanza errores porque no puede cumplir métodos del padre.
    
- Las clases hijas rompen reglas del tipo base.
    

Ejemplo conceptual:  
Una clase “Ave” no debería tener un método “volar” si existen aves que no vuelan.

---

## 4. Interface Segregation Principle (ISP)

Los clientes no deben depender de interfaces que **no utilicen**.  
Es mejor tener varias interfaces pequeñas que una sola extremadamente grande.

Evita:

- Interfaces con métodos inútiles.
    
- Implementaciones obligadas a definir funciones que no necesitan.
    

Ejemplo conceptual:  
Una interfaz “Operaciones” con métodos “imprimir”, “escaneo” y “fax” obliga a implementar métodos que tal vez no apliquen en todas las clases.  
Separar en interfaces pequeñas es más correcto.

---

## 5. Dependency Inversion Principle (DIP)

Los módulos de alto nivel no deben depender de módulos de bajo nivel.  
Ambos deben depender de **abstracciones**, no de implementaciones concretas.

Aplicación común:

- Inyección de dependencias.
    
- Uso de interfaces o clases abstractas en lugar de instancias concretas.
    

Evita:

- Código rígido acoplado a implementaciones específicas.
    
- Imposibilidad de reemplazar módulos (ideal para testing y escalabilidad).
    

---

## Resumen de aplicación práctica

- SRP: divide responsabilidades según roles claros.
    
- OCP: agrega funciones sin modificar lo existente.
    
- LSP: mantén coherente la herencia.
    
- ISP: interfaces pequeñas y específicas.
    
- DIP: usa abstracciones para reducir el acoplamiento.
    

---

## Relación con arquitectura

- En Clean Architecture estos principios son fundamentales.
    
- En MVC, SRP y OCP se aplican dividendo controladores, servicios y modelos.
    
- En APIs grandes, DIP permite reemplazar bases de datos, servicios externos o controladores sin romper el sistema.
    

Conectar con:  
[[Patrones de Software]]  
[[Ciclo de Vida del Software (SDLC)]]  
[[Buenas Practicas Codigo]]

---

## Recomendaciones

- Aplicar SOLID incluso en proyectos pequeños para mantener orden desde el inicio.
    
- Revisar clases y módulos para identificar violaciones comunes.
    
- Documentar dependencias entre capas en el diseño del proyecto.
    
- Evitar clases “Dios” con múltiples responsabilidades.