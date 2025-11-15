## Concepto general

Una arquitectura orientada a pruebas (testable architecture) es aquella que facilita escribir y ejecutar pruebas de forma sencilla, aislada y confiable.  
No se trata solo de agregar tests, sino de diseñar el sistema desde el principio para que sea facil probar sus partes criticas.

Objetivos principales:

- Poder probar la logica de negocio sin necesidad de levantar toda la aplicacion.
    
- Reducir el acoplamiento entre capas.
    
- Facilitar el uso de mocks, stubs y dobles de prueba.
    

---

## Principios basicos para codigo testeable

1. Separar logica de negocio de detalles tecnicos.
    
2. Evitar dependencias rigidas (por ejemplo, conexiones directas a BD dentro de la logica).
    
3. Diseñar funciones y metodos con entradas y salidas claras.
    
4. Mantener responsabilidad unica en clases y modulos (relacion directa con SOLID).
    
5. Usar inyeccion de dependencias cuando sea necesario.
    

---

## Logica pura vs efectos externos

Concepto clave:

- Logica pura: codigo que dado un conjunto de entradas produce salidas predecibles sin depender del entorno (sin red, sin disco, sin tiempo real).
    
- Efectos externos: operaciones que dependen de elementos externos (BD, APIs, sistema de archivos, tiempo, entorno).
    

Recomendacion:

- Concentrar la logica pura en servicios, helpers o funciones reutilizables.
    
- Encapsular los efectos externos en adaptadores, repositorios o gateways.
    

Beneficio:

- La logica pura es facil de probar con pruebas unitarias.
    
- Los efectos externos se pueden simular con mocks en las pruebas.
    

---

## Inyeccion de dependencias

La inyeccion de dependencias (DI) consiste en entregar a un modulo sus dependencias desde afuera, en lugar de que las cree el mismo.

Ejemplo conceptual:  
En lugar de:

- El servicio crea directamente una conexion a BD dentro de su codigo.
    

Se prefiere:

- El servicio recibe un repositorio o un cliente de BD como parametro o constructor.
    

Ventajas:

- Facilita reemplazar implementaciones reales por dobles de prueba.
    
- Permite cambiar la tecnologia (por ejemplo, tipo de BD) sin reescribir logica de negocio.
    
- Reduce el acoplamiento.
    

Relacion con DIP (Dependency Inversion Principle):

- Los modulos de alto nivel dependen de abstracciones, no de implementaciones concretas.
    

---

## Estructura basica orientada a pruebas

Ejemplo generico de organizacion:

/project  
├─ /src  
│ ├─ /presentation  
│ │ └─ controllers  
│ ├─ /application  
│ │ └─ services  
│ ├─ /domain  
│ │ └─ entities  
│ └─ /infrastructure  
│ └─ repositories  
└─ /tests  
├─ /unit  
├─ /integration  
└─ /e2e

Puntos clave:

- El codigo de produccion vive en /src.
    
- Las pruebas viven en /tests, siguiendo una estructura similar.
    
- Las pruebas unitarias se enfocan en servicios, helpers y logica de dominio.
    
- Las pruebas de integracion se enfocan en como se conectan servicios, repositorios y BD.
    

---

## Tipos de pruebas y capas que alcanzan

1. Pruebas unitarias
    
    - Alcance: funciones, metodos, servicios individuales.
        
    - Objetivo: validar logica aislada.
        
    - Capa principal: aplicacion y dominio.
        
2. Pruebas de integracion
    
    - Alcance: interaccion entre servicios y repositorios, APIs con BD.
        
    - Objetivo: comprobar que los componentes funcionan correctamente juntos.
        
3. Pruebas end-to-end (E2E)
    
    - Alcance: flujo completo (cliente → API → BD → respuesta).
        
    - Objetivo: revisar el sistema desde el punto de vista del usuario.
        

Relacion con arquitectura:

- Una estructura por capas clara permite decidir facilmente donde aplicar cada tipo de prueba.
    

---

## Controladores delgados y servicios probables

Parte importante de una arquitectura testeable es mantener los controladores “delgados” y los servicios “probables”.

Controladores delgados:

- Reciben la peticion.
    
- Validan parametros basicos.
    
- Llaman a un servicio.
    
- Devuelven respuesta.
    

Servicios probables:

- No dependen directamente de HTTP, objetos de request o response.
    
- Reciben datos ya validados o normalizados.
    
- Devuelven resultados en estructuras simples (objetos, listas, codigos de estado logicos).
    

Beneficio:

- Los servicios pueden probarse sin necesidad de levantar el servidor web.
    

---

## Uso de interfaces y abstracciones

Interfaz o contrato:

- Define que operaciones se pueden realizar (por ejemplo, metodos de un repositorio).
    

Ejemplo conceptual:

- IUserRepository con metodos: createUser, findByEmail, updateUser.
    

En produccion:

- Implementacion real que habla con la base de datos.
    

En pruebas:

- Implementacion falsa (mock) que devuelve datos controlados.
    

Ventajas:

- Permite probar logica de negocio sin una base de datos real.
    
- Facilita escribir pruebas rapidas y confiables.
    

---

## Manejo de tiempo, entorno y valores globales

Elementos como:

- Fecha y hora actual.
    
- Variables de entorno.
    
- Identificadores unicos.
    

Dificultan pruebas si se usan directamente en la logica.

Recomendacion:

- Encapsular estos valores en servicios o helpers.
    
- Permitir inyectar implementaciones alternativas en pruebas (por ejemplo, un “reloj” de prueba que siempre devuelve la misma hora).
    

---

## Pruebas y seguridad

Relacion con seguridad:

- Una arquitectura testeable facilita agregar pruebas especificas de seguridad:
    
    - Pruebas para verificar que ciertos endpoints requieren autenticacion.
        
    - Pruebas para confirmar que roles y permisos se aplican correctamente.
        
    - Pruebas de validacion de entradas (evitar inyecciones comunes).
        

Ademas:

- Un codigo altamente acoplado suele tener mas puntos ciegos, lo que aumenta el riesgo de fallos de seguridad.
    

---

## Recomendaciones para aplicar en proyectos nuevos

1. Definir desde el inicio la estructura de capas.
    
2. Diseñar servicios sin depender de frameworks especificos siempre que sea posible.
    
3. Evitar logica de negocio dentro de controladores o modelos de BD.
    
4. Introducir interfaces para repositorios y servicios criticos.
    
5. Crear la carpeta /tests desde el primer dia, aunque inicialmente tenga pocos archivos.
    
6. Escribir al menos algunas pruebas unitarias basicas para funcionalidad clave.
    

---

## Recomendaciones para proyectos existentes

1. Identificar las partes mas criticas del sistema (autenticacion, pagos, autorizacion).
    
2. Extraer logica de negocio hacia servicios separados.
    
3. Introducir tests unitarios progresivamente.
    
4. Refactorizar codigo muy acoplado a frameworks.
    
5. Documentar que partes del sistema tienen cobertura de pruebas y cuales no.
    

---

## Relacion con otras notas

- [[Principios SOLID]]
    
- [[Capas de una aplicacion]]
    
- [[Arquitectura de controladores y servicios]]
    
- [[Buenas Practicas Codigo]]
    
- [[Seguridad y Pentesting]]