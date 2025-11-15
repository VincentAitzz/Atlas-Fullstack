## Concepto general

JavaScript es el lenguaje de programacion que permite agregar interactividad y logica a las paginas web.  
En el contexto del frontend, JavaScript se ejecuta en el navegador y puede:

- Manipular el DOM (agregar, quitar o modificar elementos HTML).
    
- Responder a eventos del usuario (clicks, teclas, scroll).
    
- Comunicarse con servidores mediante peticiones HTTP (APIs).
    
- Almacenar datos temporalmente en el navegador.
    

---

## Estructura basica de uso

JavaScript se puede incluir de varias formas.

### 1. Archivo externo (recomendado)

```html
<!DOCTYPE html> 
<html lang="es">   
<head>     
	<meta charset="UTF-8">     
	<title>Ejemplo JS</title>   
</head>   
<body>     
	<h1 id="titulo">Hola</h1>     
	<script src="app.js"></script>   
</body> 
</html>
```

```js
// archivo app.js
console.log("JavaScript cargado");
```

Ventajas:

- Separa logica del contenido.
    
- Reutilizable y mas mantenible.
    

---

### 2. Script embebido

```html
<script>   console.log("Script dentro del HTML"); </script>
```

Util para ejemplos simples o pruebas rapidas.

---

## Variables y tipos basicos

Declaracion de variables:

```js
let nombre = "Aitzz";   // variable que puede cambiar 
const PI = 3.14159;       // constante
```

Tipos primitivos principales:

- string: texto.
    
- number: numeros.
    
- boolean: true o false.
    
- null y undefined.
    

Ejemplos:

```js
let edad = 25; 
let esAdmin = false; 
let mensaje = "Meo pene"; 
let valorNulo = null; 
let noDefinido; // undefined
```

---

## Condicionales

```js
let edad = 20;  
if (edad >= 18) {   
	console.log("Es mayor de edad"); 
} else {   
	console.log("Es menor de edad"); 
}
```

Operador ternario (version corta):

```js
let mensaje = edad >= 18 ? "Mayor" : "Menor";
```

---

## Funciones

Definen bloques reutilizables de codigo.

```js
function saludar(nombre) {   
	console.log("Hola " + nombre); 
}  
saludar("Aitzz");
```

Funciones flecha:

```js
const sumar = (a, b) => {   
	return a + b;
};  
const resultado = sumar(2, 3); // 5
```

---

## Arreglos y objetos

### Arreglos

```js
const numeros = [1, 2, 3, 4];  
console.log(numeros[0]); // 1  
numeros.push(5);         // agrega al final
```

Recorrer un arreglo:

```js
numeros.forEach((n) => {   
	console.log(n); 
});
```

### Objetos

```js
const usuario = {   
	nombre: "Vicente",   
	edad: 25,   
	esAdmin: false, 
};  
console.log(usuario.nombre); // "Vicente"
```

---

## DOM: seleccion de elementos

El DOM representa la estructura HTML como un arbol de nodos que JavaScript puede manipular.

Seleccionar elementos:

```html
<h1 id="titulo">Titulo original</h1> 
<p class="texto">Parrafo 1</p> 
<p class="texto">Parrafo 2</p>
```

```js
// Por id 
const titulo = document.getElementById("titulo");  
// Por clase 
const parrafos = document.getElementsByClassName("texto");  
// Selectores modernos 
const primerParrafo = document.querySelector(".texto"); 
const todosParrafos = document.querySelectorAll(".texto");
```

---

## DOM: modificar contenido y estilos

Modificar texto:

```js
titulo.textContent = "Nuevo titulo"; 
primerParrafo.innerHTML = "<strong>Texto en negrita</strong>";
```

Modificar estilos:

```js
titulo.style.color = "blue"; 
titulo.style.fontSize = "24px";
```

Agregar o quitar clases:

```js
titulo.classList.add("activo"); 
titulo.classList.remove("activo"); 
titulo.classList.toggle("resaltado");
```

---

## Manejo de eventos

Los eventos permiten responder a acciones del usuario.

HTML de ejemplo:

```html
<button id="boton">Haz click</button> 
<p id="resultado"></p>
```

JavaScript:

```js
const boton = document.getElementById("boton");
const resultado = document.getElementById("resultado");  boton.addEventListener("click", () => {   
	resultado.textContent = "Boton pulsado"; 
});
```

Eventos comunes:

- click
    
- input
    
- submit
    
- keydown / keyup
    
- mouseover / mouseout
    

Ejemplo con formulario:

```html
<form id="login">   
	<input id="email" type="email" placeholder="Email">   
	<input id="password" type="password" placeholder="Contraseña">   
	<button type="submit">Entrar</button> 
</form> 
<p id="mensaje"></p>
```

```js
const form = document.getElementById("login"); 
const mensaje = document.getElementById("mensaje");  form.addEventListener("submit", (event) => {   
	event.preventDefault(); // evitar recarga de pagina    
	const email = document.getElementById("email").value;   
	mensaje.textContent = "Intentando login con " + email; 
});
```

---

## Comunicacion con APIs (fetch basico)

JavaScript puede hacer peticiones HTTP desde el navegador usando `fetch`.

Ejemplo de peticion GET:

```js
fetch("https://jsonplaceholder.typicode.com/posts/1")
.then((response) => response.json())   
.then((data) => {     
	console.log("Datos recibidos:", data);   
}).catch((error) => {     
	console.error("Error al llamar API:", error);   
});
```

Version con async/await:

```js
async function cargarPost() {   
	try {     
		const response = await fetch("https://jsonplaceholder.typicode.com/posts/1");
		const data = await response.json();     
		console.log("Datos:", data);   
	} catch (error) {     
		console.error("Error:", error);   
	} 
} 
cargarPost();
```

Integrado con el DOM:

```html
<button id="cargar">Cargar datos</button>
<pre id="salida"></pre>
```

```js
const botonCargar = document.getElementById("cargar");
const salida = document.getElementById("salida");  botonCargar.addEventListener("click", async () => {   
	try {     
		const response = await fetch("https://jsonplaceholder.typicode.com/posts/1");     
		const data = await response.json();     
		salida.textContent = JSON.stringify(data, null, 2);   
	} catch (error) {     
		salida.textContent = "Error al obtener datos";   
	} 
});
```

---

## Buenas practicas basicas en JavaScript

- Usar `const` por defecto y `let` cuando realmente cambie el valor.
    
- Evitar variables globales innecesarias.
    
- Nombrar variables y funciones de forma descriptiva.
    
- Separar logica en funciones pequeñas y reutilizables.
    
- Manejar errores en operaciones asincronas (`try/catch` o `.catch`).
    
- Mantener el codigo organizado en modulos o archivos separados.
    

Relacion con otras notas:

- [[Fundamentos HTML]]
    
- [[Fundamentos CSS]]
    
- [[Diseño de APIs]]
    
- [[Buenas Practicas Codigo]]
    
- [[Arquitectura de Aplicaciones Web Modernas]]
    

---

## Recomendaciones para practica

- Practicar seleccionando elementos del DOM y cambiando su contenido.
    
- Crear botones que cambien estilos o muestren/oculten secciones.
    
- Implementar un pequeño formulario que muestre los datos ingresados en pantalla sin recargar la pagina.
    
- Hacer una llamada sencilla a una API publica y mostrar el resultado en el HTML.