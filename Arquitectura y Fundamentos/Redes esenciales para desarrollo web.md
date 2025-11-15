## Concepto general

Las redes son la base de cualquier aplicacion web.  
Entender como viajan los datos desde el cliente hasta el servidor y de vuelta es fundamental tanto para desarrollar como para analizar la seguridad de un sistema.

Este documento resume los conceptos de redes mas importantes para desarrollo web moderno.

---

## Direcciones IP y puertos

### Direccion IP

Una direccion IP identifica un dispositivo en una red.

Tipos principales:

- IPv4: formato 192.168.0.1
    
- IPv6: formato extendido, menos usado directamente en desarrollo basico
    

Clasificacion util para desarrollo:

- Localhost: 127.0.0.1 (equipo local)
    
- Redes privadas: 192.168.x.x, 10.x.x.x
    
- Direccion publica: IP accesible desde internet
    

### Puertos

Un puerto identifica un servicio dentro de un mismo host.

Ejemplos tipicos:

- 80: HTTP
    
- 443: HTTPS
    
- 22: SSH
    
- 5432: PostgreSQL
    
- 3306: MySQL
    
- 6379: Redis
    

En desarrollo:

- Es comun exponer aplicaciones web en puertos como 3000, 8000, 8080, etc.
    

---

## HTTP y HTTPS

### HTTP

Protocolo de comunicacion entre cliente y servidor en la web.

Caracteristicas:

- Basado en peticiones y respuestas.
    
- Texto plano por defecto.
    
- No cifrado.
    

Una peticion HTTP incluye:

- Metodo (GET, POST, etc.).
    
- URL.
    
- Headers.
    
- Cuerpo (opcional).
    

### HTTPS

Es HTTP sobre TLS/SSL, es decir, HTTP cifrado.

Beneficios:

- Confidencialidad: los datos viajan cifrados.
    
- Integridad: se evita manipulacion de datos en el medio.
    
- Autenticacion: uso de certificados para validar servidor.
    

Recomendacion:

- En entornos reales, siempre usar HTTPS.
    
- En desarrollo, usarlo al menos para pruebas que involucren autenticacion.
    

---

## DNS (Domain Name System)

El DNS traduce nombres de dominio legibles (ej: midominio.com) a direcciones IP.

Importancia en desarrollo:

- Permite separar frontend, backend y servicios en diferentes dominios o subdominios.
    
- Util en configuraciones de CORS, cookies, proxies y certificados.
    

Ejemplo:

- api.miaplicacion.com → API backend
    
- app.miaplicacion.com → frontend
    

---

## Conceptos de red basicos aplicados a desarrollo

### Cliente y servidor

- Cliente: quien hace la peticion (navegador, aplicacion movil, Postman).
    
- Servidor: quien procesa la peticion y responde (backend, API, servicio).
    

### Request y response

- Cada operacion entre cliente y servidor se basa en:
    
    - Peticion (request).
        
    - Respuesta (response).
        

La peticion incluye:

- Metodo HTTP.
    
- URL.
    
- Headers (autorizacion, content-type).
    
- Cuerpo (datos).
    

La respuesta incluye:

- Codigo de estado.
    
- Headers.
    
- Cuerpo (datos, mensajes, errores).
    

---

## CORS (Cross-Origin Resource Sharing)

CORS define si un navegador permite que una pagina cargada desde un dominio haga peticiones a otro dominio.

Ejemplo de origen:

- https://miapp.com
    
- http://localhost:3000
    

Problema comun:

- Frontend en http://localhost:3000 y backend en http://localhost:8000
    
- El navegador puede bloquear la peticion si el servidor no configura CORS correctamente.
    

Desde el lado del servidor:

- Se configuran headers como:
    
    - Access-Control-Allow-Origin
        
    - Access-Control-Allow-Methods
        
    - Access-Control-Allow-Headers
        

CORS es un tema clave tanto en desarrollo como en pruebas de seguridad.

---

## Cookies, sesiones y tokens

### Cookies

Pequeños datos almacenados en el navegador y enviados automaticamente al servidor en cada peticion al mismo dominio.

Uso tipico:

- Manejo de sesiones.
    
- Preferencias de usuario.
    

Propiedades importantes:

- HttpOnly: evita acceso desde JavaScript.
    
- Secure: solo se envia por HTTPS.
    
- SameSite: controla envio en peticiones cross-site.
    

### Sesiones

- El servidor mantiene informacion asociada a un usuario.
    
- El cliente envia un identificador (por ejemplo, en una cookie).
    
- La sesion vive en el servidor o en un almacen centralizado.
    

### Tokens (JWT)

- Son cadenas firmadas que contienen informacion del usuario (claims).
    
- Se pueden enviar en headers (Authorization: Bearer <token>).
    
- No requieren almacenar estado de sesion en el servidor.
    

Relacion con seguridad:

- Un mal manejo de cookies, sesiones o tokens abre puertas a ataques como secuestro de sesion, XSS o CSRF.
    

---

## Proxies y reverse proxies

### Proxy

- Cliente → Proxy → Servidor
    
- El cliente se comunica con el proxy, que reenvia la peticion al destino.
    

Usos:

- Filtrado de trafico.
    
- Inspeccion.
    
- Cache.
    

### Reverse proxy

- Cliente → Reverse Proxy → uno o varios servidores internos.
    

Usos:

- Balanceo de carga.
    
- Terminacion TLS (cifrado).
    
- Redireccion segun ruta o dominio.
    

Ejemplos: Nginx, Apache, Traefik.

En desarrollo:

- Comun en despliegues modernos y en arquitecturas con multiples servicios.
    

---

## NAT y redes locales

NAT (Network Address Translation):

- Permite que varios dispositivos en una red privada compartan una misma IP publica.
    

En desarrollo:

- Normal cuando trabajas detras de un router domestico.
    
- Las aplicaciones pueden estar accesibles solo en la red local (192.168.x.x).
    

Importante:

- Diferenciar entre servicios que corren solo en localhost y servicios accesibles desde la red.
    

---

## WebSockets y comunicacion en tiempo real

HTTP clasico:

- Peticion-respuesta, conexion de corta duracion.
    

WebSockets:

- Conexion persistente entre cliente y servidor.
    
- Permite enviar datos en ambas direcciones sin nuevas peticiones HTTP.
    

Usos:

- Chats.
    
- Notificaciones en tiempo real.
    
- Actualizaciones dinamicas.
    

Relacion con desarrollo y seguridad:

- Requiere gestionar autenticacion persistente.
    
- Debe protegerse frente a conexiones no autorizadas.
    

---

## Herramientas basicas para analizar redes

Para desarrollo y pentesting, es util conocer:

- ping: comprobar conectividad.
    
- traceroute / tracert: rastrear ruta de paquetes.
    
- netstat o ss: ver puertos abiertos.
    
- curl: hacer peticiones HTTP desde consola.
    
- Postman o similares: probar APIs.
    
- Navegador (pestaña Network en devtools): inspeccionar peticiones.
    

En entornos de pruebas de seguridad:

- Burp Suite, OWASP ZAP: interceptar y modificar trafico HTTP/HTTPS.
    

---

## Relacion con desarrollo web y pentesting

Desarrollo:

- Configurar correctamente puertos, dominios, CORS y HTTPS.
    
- Entender por que una peticion falla a nivel de red.
    
- Diseñar APIs compatibles con redes reales (proxies, balanceadores, etc.).
    

Pentesting:

- Identificar servicios expuestos.
    
- Analizar puertos y protocolos.
    
- Entender donde se data expuesta o sin cifrar.
    
- Detectar errores de configuracion (CORS, cookies, headers de seguridad).
    

---

## Recomendaciones finales

- Tener claridad sobre donde corre cada servicio (IP, puerto).
    
- Usar siempre HTTPS en entornos reales.
    
- Configurar CORS de forma explicita y no completamente abierta sin motivo.
    
- Entender minimamente DNS, IP, puertos y proxies antes de desplegar.
    
- Apoyarse en herramientas de red para diagnosticar problemas y pruebas de seguridad.
    

Relacion con otras notas:

- [[Arquitectura de Aplicaciones Web Modernas]]
    
- [[Diseño de APIs]]
    
- [[Seguridad y Pentesting]]
    
- [[Buenas Practicas Codigo]]