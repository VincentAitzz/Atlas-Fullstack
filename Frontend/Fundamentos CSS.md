## Concepto general

CSS (Cascading Style Sheets) es el lenguaje que define la presentacion de un documento HTML.  
Permite controlar colores, tamaños, fuentes, distribucion de elementos, espaciados y comportamiento visual en distintos dispositivos.

HTML define la estructura.  
CSS define la apariencia.

---

## Formas de aplicar CSS

### 1. CSS externo (recomendado)

Archivo .css separado, enlazado desde el HTML.

```html
<!DOCTYPE html>
<html lang="es">   
<head>     
	<meta charset="UTF-8">     
	<title>Ejemplo</title>     
	<link rel="stylesheet" href="styles.css">   
</head>   
<body>     
	<h1>Hola mundo</h1>   
</body> 
</html>
```

```css
/* archivo styles.css */
h1 {   
	color: blue;
}
```

Ventajas:

- Separacion clara entre estructura (HTML) y estilos (CSS).
    
- Mas facil de mantener y reutilizar.
    

---

### 2. CSS en el head (estilos internos)

Usando la etiqueta `<style>` dentro de `<head>`.

```html
<head>   
<style>     
	h1 {       
		color: red;     
	}   
</style> 
</head>
```

Util en ejemplos pequeños o prototipos, pero no ideal para proyectos grandes.

---

### 3. Estilos en linea (inline)

Usando el atributo `style` directamente en el elemento.

```html
<h1 style="color: green; font-size: 24px;">Titulo</h1>
```

Desventajas:

- Dificil de mantener.
    
- Mezcla contenido y estilos.  
    Se recomienda evitarlo salvo casos muy puntuales.
    

---

## Selectores basicos

Los selectores indican a que elementos se aplica un bloque de estilos.

### Por etiqueta

Selecciona todos los elementos de ese tipo.

```css
p {   
	color: #333; 
}
```

### Por clase

Usa un punto `.` y se aplica a elementos con esa clase.

```html
<p class="destacado">Texto destacado</p>
```

```css
.destacado {   
	font-weight: bold; 
}
```

### Por id

Usa numeral `#` y se aplica a un elemento con id unico.

```html
<p id="mensaje">Hola</p>
```

```css
#mensaje {   
	color: red; 
}
```

### Combinados y otros ejemplos

```css
/* Todos los parrafos dentro de un div */ 
div p {   
	margin-bottom: 8px; 
}  
/* Todos los enlaces dentro de la navegacion */ 
nav a {   
	text-decoration: none; 
}  
/* Multiples elementos con el mismo estilo */ 
h1, h2, h3 {   
	font-family: Arial, sans-serif; 
}
```

---

## Propiedades basicas

Algunas propiedades muy usadas:

```css
selector {
	/* color del texto */  
	color: #000000;           
	/* color de fondo */   
	background-color: #f5f5f5;
	/* tamaño de fuente */   
	font-size: 16px;          
	/* grosor de fuente */   
	font-weight: bold;        
	/* alineacion de texto */   
	text-align: center;       
	/* margen externo */   
	margin: 16px;             
	/* relleno interno */   
	padding: 8px;             
	/* borde */ 
	border: 1px solid #ccc;   
}
	```

---

## El modelo de caja (Box Model)

Cada elemento en CSS se representa como una caja formada por:

- content (contenido).
    
- padding (espacio interno).
    
- border (borde).
    
- margin (espacio externo respecto a otros elementos).
    

Ejemplo grafico en codigo:

```css
.caja {   
	/* ancho del contenido */   
	width: 200px;             
	/* espacio interno */   
	padding: 10px;            
	/* borde */   
	border: 2px solid #000;   
	/* espacio externo */
	margin: 20px;             
}
```

Por defecto, `width` y `height` afectan solo al contenido.  
Se puede cambiar este comportamiento con `box-sizing`:

```css
.caja {   
	box-sizing: border-box; 
}
```

Con `border-box`, el ancho total incluye padding y borde, lo que facilita maquetar.

---

## Display: block, inline e inline-block

### block

Ocupa todo el ancho disponible y comienza en una nueva linea.

Ejemplos tipicos: `div`, `p`, `h1`.

```css
div {   
	display: block; 
}
```

### inline

No inicia nueva linea, solo ocupa el ancho necesario.

Ejemplos tipicos: `span`, `a`.

```css
span {   
	display: inline; 
}
```

### inline-block

Se comporta como inline pero acepta width, height, margin, etc.

```css
.boton {   
	display: inline-block;   
	padding: 8px 16px; 
}
```

---

## Posicionamiento basico

Propiedad `position`:

- static (por defecto).
    
- relative.
    
- absolute.
    
- fixed.
    
- sticky.
    

Ejemplo simple:

```css
.contenedor {   
	position: relative; 
}  
.caja-absoluta {   
	position: absolute;   
	top: 10px;   
	right: 10px; 
}
```

La caja absoluta se posiciona respecto al contenedor relativo.

---

## Flexbox (introduccion)

Flexbox facilita la distribucion de elementos en una dimension (fila o columna).

Estructura basica:

```html
<div class="contenedor">   
	<div class="item">1</div>   
	<div class="item">2</div>   
	<div class="item">3</div> 
</div>
```

```css
.contenedor {   
	/* activa flexbox */   
	display: flex;            
	/* espacio entre items */ 
	gap: 10px;                
}  
.item {   
	background-color: #ddd;   
	padding: 10px; 
}
```

Alineacion horizontal y vertical:

```css
.contenedor {   
	display: flex;   
	/* alinea en el eje principal */   
	justify-content: center;  
	/* alinea en el eje cruzado */ 
	align-items: center;      
}
```

Direccion:

```css
.contenedor {   
	display: flex;   
	/* por defecto es row */ 
	flex-direction: column;   
}
```

---

## Responsive design (introduccion)

El diseño responsive adapta la interfaz a distintos tamaños de pantalla.

Tecnica principal: media queries.

```css
body {   
	font-size: 16px; 
}  
/* Estilos para pantallas maximo 600px de ancho */ 
@media (max-width: 600px) {   
	body {     
		font-size: 14px;   
	}    
	.contenedor {     
		flex-direction: column;   
	} 
}
```

Tambien se utilizan unidades relativas:

- `%`
    
- `em`, `rem`
    
- `vw`, `vh`
    

---

## Buenas practicas CSS

- Mantener estilos en archivos externos.
    
- Usar nombres de clases descriptivos.
    
- Evitar depender de ids para estilos reutilizables.
    
- No abusar de selectores demasiado especificos.
    
- Agrupar estilos relacionados.
    
- Eliminar estilos muertos o no usados cuando el proyecto crezca.
    

Relacion con otras notas:

- [[Fundamentos HTML]]
    
- [[Fundamentos JavaScript]]
    
- [[Buenas Practicas Codigo]]
    
- [[Arquitectura de Aplicaciones Web Modernas]]
    

---

## Recomendaciones para practica

- Crear una pagina simple y aplicar estilos basicos (colores, fuentes, margenes).
    
- Practicar con el modelo de caja: borders, padding, margin, box-sizing.
    
- Crear un layout simple usando flexbox (barra de navegacion, contenido y pie de pagina).
    
- Usar las herramientas de desarrollo del navegador para inspeccionar estilos y cajas.