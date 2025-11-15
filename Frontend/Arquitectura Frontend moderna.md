## Concepto general

La arquitectura frontend moderna describe como se organiza, estructura y ejecuta el codigo que se encarga de la interfaz de usuario en aplicaciones web actuales.

A diferencia de las paginas tradicionales (generadas totalmente en el servidor), el frontend moderno suele:

- Ejecutarse en gran parte en el navegador.
    
- Manejar estado de la aplicacion en el cliente.
    
- Comunicarse constantemente con APIs.
    
- Usar componentes reutilizables en lugar de paginas estaticas.
    

---

## MPA vs SPA

### MPA (Multi-Page Application)

- Cada pagina se carga desde el servidor.
    
- Navegar implica nuevas peticiones completas (HTML nuevo).
    
- Ejemplo clasico: sitios hechos solo con HTML+CSS+un poco de JS, o frameworks como Django/Laravel renderizando plantillas.
    

Ventajas:

- Simples de entender.
    
- Buen SEO por defecto.
    

Desventajas:

- Navegacion mas lenta (recarga completa).
    
- Manejo de estado en cliente mas limitado.
    

### SPA (Single-Page Application)

- La aplicacion se carga una vez (HTML base + JS).
    
- Las vistas cambian dinamicamente en el navegador sin recargar toda la pagina.
    
- El routing se maneja en el cliente (JavaScript).
    

Ventajas:

- Experiencia de usuario mas fluida.
    
- Navegacion rapida entre vistas.
    
- Facil integracion con APIs.
    

Desventajas:

- Mas complejidad inicial.
    
- SEO mas complejo (aunque hay soluciones como SSR y SSG).
    

---

## Componentes

La unidad principal de organizacion en frontend moderno es el componente.

Un componente suele agrupar:

- HTML (estructura).
    
- CSS (estilo).
    
- JavaScript (logica).
    

Por ejemplo, un componente de tarjeta de usuario, boton, formulario, barra de navegacion, etc.

Caracteristicas de un buen componente:

- Reutilizable.
    
- Encapsulado (su estilo y logica no interfieren con otros componentes).
    
- Claro en su responsabilidad (hace una cosa bien definida).
    

Estructura conceptual de un proyecto basado en componentes:

```dir
/src   
	/components     
		Button     
		Navbar     
		UserCard   
	/pages     
		Home     
		Login     
		Dashboard   
	/services     
		apiClient   
	/styles   
	main.(js|ts)
```

---

## Estado en el frontend

El estado es la informacion que la interfaz necesita para saber que mostrar en cada momento.

Tipos de estado:

1. Estado local
    
    - Propio de un componente.
        
    - Ejemplo: valor de un input, si un modal esta abierto, etc.
        
2. Estado compartido
    
    - Usado por varios componentes.
        
    - Ejemplo: usuario logueado, tema oscuro/claro, items de un carrito.
        
3. Estado derivado
    
    - Calculado a partir de otros estados.
        
    - Ejemplo: total del carrito a partir de la lista de productos.
        

En frameworks modernos, el manejo de estado se hace mediante:

- Hooks, stores o librerias especificas (segun el framework).
    

Principio importante:

- Mantener el estado lo mas cerca posible de donde se usa.
    
- Solo elevar el estado cuando de verdad sea compartido.
    

---

## Comunicacion con APIs

En una arquitectura frontend moderna, el cliente no habla con la base de datos.  
Se comunica con un backend a traves de APIs (normalmente REST o GraphQL).

Patron comun:

- Crear un modulo o servicio de API para centralizar las llamadas.
    

Ejemplo generico:

```js
// apiClient.js 
const API_URL = "https://api.ejemplo.com";  
export async function getUsuarios() {   
	const response = await fetch(`${API_URL}/users`);   
	if (!response.ok) {     
		throw new Error("Error al obtener usuarios");   
	}   
	return response.json(); 
}
```

Beneficios:

- Las llamadas a la API estan en un unico lugar.
    
- Facil de manejar errores, autenticacion y cabeceras.
    
- Facil de reutilizar en distintos componentes.
    

Relacion directa con:

- [[Diseño de APIs]]
    
- [[Redes esenciales para desarrollo web]]
    

---

## Routing en el frontend

En una SPA, el routing no se basa en recargar paginas completas, sino en cambiar vistas internamente.

Conceptos clave:

- El navegador cambia la URL.
    
- El framework de frontend decide que componente renderizar segun la ruta.
    
- Se puede usar el History API (pushState) para cambiar rutas sin recargar.
    

Ejemplo conceptual (no ligado a un framework concreto):

```dir
/          -> HomePage
/login    -> LoginPage 
/dashboard -> DashboardPage
```

El router interno del frontend:

- Escucha cambios de ruta.
    
- Renderiza el componente correspondiente.
    

---

## Assets, build y bundlers

En proyectos modernos, el codigo no se sirve tal cual lo escribes, sino que pasa por un proceso de build.

Conceptos importantes:

- Bundlers: herramientas que empaquetan muchos archivos en uno o varios archivos optimizados.
    
    - Ejemplos: Webpack, Vite, Parcel.
        
- Transpiladores: convierten versiones modernas de JS/TS a versiones compatibles con mas navegadores.
    
    - Ejemplos: Babel, TypeScript.
        
- Minificacion: reducir tamaño de archivos (eliminar espacios, comentarios, etc.).
    
- Assets: imagenes, fuentes, iconos, estilos globales.
    

Estructura generica:

```txt
/project   
	/src     
		...codigo fuente...   
	/public     
		index.html   
	/dist (o /build)     
		...codigo optimizado para produccion...
```

---

## Estilos en arquitecturas modernas

Formas comunes de manejar estilos:

1. CSS clasico (archivos .css separados).
    
2. Preprocesadores (Sass, Less).
    
3. CSS Modules (estilos asociados a componentes).
    
4. CSS-in-JS (estilos definidos en JS/TS, segun el framework).
    
5. Frameworks de estilos (Tailwind, Bootstrap, etc.).
    

Principios:

- Evitar estilos globales excesivos que choquen entre si.
    
- Priorizar estilos encapsulados por componente cuando el framework lo permita.
    
- Mantener una paleta y sistema de diseño consistente.
    

Relacion con:

- [[Fundamentos CSS]]
    

---

## Arquitectura por features vs arquitectura por capas (en frontend)

Dos enfoques comunes para organizar el proyecto.

### Por capas

```
/src   
	/components   
	/pages   
	/styles   
	/services   
	/utils
```

Ventajas:

- Sencilla de entender al inicio.
    

Desventajas:

- Cuando el proyecto crece, puede ser dificil encontrar todo lo relacionado a una feature.
    

### Por features o dominios

```
/src   
	/features     
	/auth       
		components       
		services       
		pages     
	/users       
		components       
		services       
		pages   
	/shared     
		components     
		utils     
		styles
```

Ventajas:

- Todo lo relacionado a una feature esta junto.
    
- Facil de extraer o modificar una funcionalidad completa.
    

Desventajas:

- Mas compleja de diseñar al principio.
    

---

## Integracion con backend y seguridad

En una arquitectura frontend moderna, el frontend:

- Depende de un backend bien diseñado.
    
- Debe manejar de forma correcta:
    
    - Autenticacion (tokens, cookies).
        
    - Autorizacion (roles, permisos).
        
    - Errores de red y de API.
        

Puntos clave:

- Nunca confiar en que el frontend “protege” las reglas de negocio.
    
- Todas las validaciones criticas deben existir tambien en el backend.
    
- Evitar exponer informacion sensible en el bundle del frontend.
    

Relacion con:

- [[Arquitectura de Aplicaciones Web Modernas]]
    
- [[Redes esenciales para desarrollo web]]
    
- [[Seguridad y Pentesting]]
    

---

## Relacion con frameworks

Frameworks modernos (React, Vue, Angular, etc.) proporcionan:

- Manejo de componentes.
    
- Manejo de estado.
    
- Routing de SPA.
    
- Integracion con herramientas de build.
    

La arquitectura frontend moderna no depende de un framework especifico, pero los frameworks ayudan a implementarla de forma mas productiva.

Recomendacion:

- Entender estos conceptos antes de utilizar un framework.
    
- Ver cada framework como una herramienta para aplicar esta arquitectura, no como algo “magico”.
    

---

## Recomendaciones finales

- Pensar siempre en componentes y estado, no solo en paginas sueltas.
    
- Separar la comunicacion con la API en modulos o servicios dedicados.
    
- Definir una estructura de carpetas clara desde el inicio (por capas o por features).
    
- Aprender a usar al menos un bundler moderno (directa o indirectamente a traves de un framework).
    
- Considerar desde el inicio temas de rendimiento y seguridad (tamanio del bundle, manejo de tokens, errores).
    

Relacion con otras notas:

- [[Fundamentos HTML]]
    
- [[Fundamentos CSS]]
    
- [[Fundamentos JavaScript]]
    
- [[Arquitectura de Aplicaciones Web Modernas]]
    
- [[Diseño de APIs]]
    
- [[Redes esenciales para desarrollo web]]