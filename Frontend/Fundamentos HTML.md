## Concepto general

HTML (HyperText Markup Language) es el lenguaje que define la estructura del contenido en una pagina web.  
No es un lenguaje de programacion, sino un lenguaje de marcado que organiza el contenido mediante elementos (etiquetas).

El navegador interpreta el HTML y construye el DOM (Document Object Model), que luego puede ser estilizado con CSS y manipulado con JavaScript.

---

## Estructura basica de un documento HTML

Estructura minima de una pagina:

```html
<!DOCTYPE html>
<html lang="es">   
<head>     
	<meta charset="UTF-8">     
	<title>Titulo de la pagina</title>   
</head>   
<body>    
	Contenido visible de la pagina.   
</body> 
</html>
```

Elementos principales:

- doctype: indica que el documento usa HTML5.
    
- html: raiz del documento.
    
- head: metadata, configuraciones, enlaces a CSS, etc.
    
- body: contenido visible (texto, imagenes, enlaces, etc.).
    

---

## Elementos basicos

### Texto y estructura

Etiquetas mas comunes para texto:

- h1 a h6: titulos.
    
- p: parrafos.
    
- span: contenedor en linea sin significado semantico.
    
- div: contenedor en bloque sin significado semantico.
    

Ejemplo:

```html
<h1>Titulo principal</h1>
<p>Este es un parrafo de ejemplo.</p>
<div>  
	<p>Contenido dentro de un contenedor.</p> 
</div>
```

---

### Listas

Tipos de listas:

- ul: lista desordenada (viñetas).
    
- ol: lista ordenada (numeros).
    
- li: elemento de lista.
    

Ejemplo:

```html
<ul>
	<li>Elemento 1</li>   
	<li>Elemento 2</li> 
</ul>  
<ol>   
	<li>Paso 1</li>   
	<li>Paso 2</li> 
</ol>
```

---

### Enlaces e imagenes

Etiquetas principales:

- a: enlace.
    
- img: imagen.
    

Atributos importantes:

- href en a.
    
- src y alt en img.
    

Ejemplos:

```html
<a href="https://ejemplo.com">Ir a ejemplo</a>
<img src="imagen.jpg" alt="Descripcion de la imagen">
```

El atributo alt es importante para accesibilidad y SEO.

---

## Atributos

Los elementos HTML pueden tener atributos que modifican su comportamiento o proporcionan informacion adicional.

Atributos comunes:

- id: identificador unico.
    
- class: clase para agrupar estilos o seleccionar elementos.
    
- title: texto extra mostrado al pasar el raton.
    
- data-* : atributos personalizados de datos.
    

Ejemplo:

```html
<p id="intro" class="texto-destacado" title="Parrafo inicial">   
Hola, esto es un parrafo.
</p>
```

---

## HTML semantico

El HTML semantico usa etiquetas que describen el significado del contenido, no solo su aspecto.

Etiquetas semanticas comunes:

- header: cabecera de la pagina o seccion.
    
- nav: barra de navegacion.
    
- main: contenido principal.
    
- section: seccion generica de contenido.
    
- article: contenido independiente (post, noticia).
    
- aside: contenido relacionado (barras laterales).
    
- footer: pie de pagina.
    

Ejemplo de estructura semantica:

```html
<body>   
	<header>     
		<h1>Mi sitio web</h1>     
		<nav>       
			<a href="#inicio">Inicio</a>       
			<a href="#blog">Blog</a>     
		</nav>   
	</header>    
	<main>     
		<section id="inicio">       
			<h2>Inicio</h2>       
			<p>Contenido principal.</p>     
		</section>      
		<section id="blog">       
			<article>         
				<h3>Articulo 1</h3>         
				<p>Texto del articulo.</p>       
			</article>     
		</section>   
	</main>    
<aside>     
	<p>Contenido adicional o secundario.</p>   
</aside>    
<footer>     
	<p>Copyright 2025</p>   
</footer> 
</body>
```

Beneficios:

- Mejor accesibilidad.
    
- Mejor SEO.
    
- Codigo mas claro y mantenible.
    

---

## Formularios

Los formularios permiten enviar datos desde el cliente al servidor.

Elementos principales:

- form: contenedor de formulario.
    
- input: campo de entrada (texto, password, email, checkbox, radio, etc.).
    
- textarea: campo de texto multilinea.
    
- select: lista desplegable.
    
- button: boton.
    

Ejemplo basico:

```html
<form action="/login" method="POST">   
	<label for="email">Email</label>   
	<input id="email" name="email" type="email" required>    
	<label for="password">Contraseña</label>   
	<input id="password" name="password" type="password" required>    
	<button type="submit">Iniciar sesion</button> 
</form>
```

Ejemplo con distintos tipos de input:

```html
<form action="/registro" method="POST">   
	<label for="nombre">Nombre</label>   
	<input id="nombre" name="nombre" type="text" required>    
	<label>     
		<input type="checkbox" name="terminos" required>Acepto los terminos y condiciones  
	</label>    
	<label for="rol">Rol</label>   
	<select id="rol" name="rol">     
		<option value="user">Usuario</option>     
		<option value="admin">Administrador</option>   
	</select>    
	<button type="submit">Registrarse</button>
</form>
```

---

## Buenas practicas HTML

- Usar etiquetas semanticas siempre que sea posible.
    
- Mantener una estructura clara y consistente del documento.
    
- Evitar abusar de div y span cuando existan etiquetas mas adecuadas.
    
- Usar atributos alt en imagenes.
    
- Usar atributos id y class de forma descriptiva.
    
- Evitar estilos inline cuando sea posible; preferir CSS externo.
    

Relacion con otras notas:

- [[Fundamentos CSS]]
    
- [[Fundamentos JavaScript]]
    
- [[Arquitectura de Aplicaciones Web Modernas]]
    
- [[Buenas Practicas Codigo]]
    

---

## HTML y accesibilidad (introduccion)

Conceptos minimos:

- Usar etiquetas label asociadas a inputs mediante el atributo for.
    
- Mantener un orden logico de titulos (h1, h2, h3...).
    
- Evitar usar solo el color para transmitir informacion importante.
    
- Proporcionar alternativas textuales para imagenes y contenidos multimedia.
    

Ejemplo de label bien asociado a input:

```html
<label for="telefono">Telefono</label> 
<input id="telefono" name="telefono" type="tel">
```

---

## Recomendaciones para practica

- Crear paginas simples con estructura semantica completa (header, nav, main, section, article, aside, footer).
    
- Practicar formularios basicos (login, registro, contacto).
    
- Usar las herramientas de desarrollo del navegador para inspeccionar el DOM y entender como se organiza el documento.