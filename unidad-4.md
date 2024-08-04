* [Aplicaciones de red](#aplicaciones-de-red)
    * [Arquitecturas de aplicación](#arquitecturas-de-aplicación)
        * [Cliente-Servidor](#cliente-servidor)
        * [Peer-to-Peer (P2P)](#peer-to-peer-p2p)
        * [Híbridos de cliente-servidor y P2P](#híbridos-de-cliente-servidor-y-p2p)
* [Proceso](#proceso)
    * [Algunos puertos comunes y sus protocolos](#algunos-puertos-comunes-y-sus-protocolos)
* [Api (Interfaz de Programación de Aplicaciones)](#api-interfaz-de-programación-de-aplicaciones)
* [HTTP (HyperText Transfer Protocol)](#http-hypertext-transfer-protocol)
    * [Conexiones HTTP](#conexiones-http)
    * [Mensajes HTTP de respuesta](#mensajes-http-de-respuesta)
    * [Códigos HTTP de respuesta](#códigos-http-de-respuesta)
* [Manejo de certificados](#manejo-de-certificados)
* [Web cache](#web-cache)
* [Extras](#extras)
* [Webgrafía](#webgrafía)

# Aplicaciones de red

Corren en diferentes sistemas y se comunican por la red. Ejemplo: la web, donde un programa del servidor web se comunica con el programa del navegador.

## Arquitecturas de aplicación

### Cliente-Servidor

**Componentes**

* **Servidor**
    * Equipo siempre encendido.
    * Dirección IP permanente/fija.
    * Cluster de servidores por escalimiento.
* **Cliente**
    * Se comunica con el servidor para solicitar servicios.
    * Puede conectarse intermitentemente.
    * Puede tener direcciones IP dinámicas.

**Funcionamiento**

1. El cliente envía una solicitud al servidor.
2. El servidor procesa la solicitud y envía una respuesta de vuelta al cliente.

> **Ejemplo**: aplicaciones web tradicionales como Gmail.

> [!NOTE]
> Un **cluster de servidores por escalamiento** es un conjunto de servidores que trabajan juntos para proporcionar un servicio más robusto, escalable y de alta disponibilidad. Su objetivo es mejorar el rendimiento, manejar mayores volúmenes de tráfico, mejorar la capacidad de procesamiento de datos, y proveer contingencia en caso de fallos de software o hardware.

### Peer-to-Peer (P2P)

Cada nodo de la red actúa simultáneamente como cliente y servidor, compartiendo recursos directamente con otros nodos sin necesidad de un servidor centralizado.

**Componentes**

* **Pares (Peers)**: cada dispositivo de la red, que puede actuar tanto como cliente como servidor.

**Funcionamiento**

1. Un peer solicita un recurso a otro peer.
2. El peer que tiene el recurso responde directamente a la solicitud.

> **Ejemplo**: redes de intercambio de archivos como BitTorrent.

### Híbridos de cliente-servidor y P2P

**Componentes**

* **Servidor central**: proporciona servicios como autenticación y coordinación.
* **Peers**: comparten recursos directamente entre ellos.

**Funcionamiento**

* Los peers registran contenido en un servidor central.
* Los peers consultan al servidor central para localizar el contenido.

> **Ejemplo**: servicios de mensajería como WhatsApp, que usan servidores centrales para autenticación y coordinación, pero permiten el intercambio directo de mensajes y archivos entre usuarios.

# Proceso

Un proceso en una máquina es un programa corriendo en la misma. Este incluye el código del programa y su estado de ejecución actual.

* Los **procesos en una misma máquina** se comunican usando **comunicación entre procesos** (definida por el SO).
* Los **procesos entre distintas máquinas** se comunican vía intercambio de **mensajes**.

Para que un proceso reciba un mensaje, el mismo precisa de un identificador, el cual se compone de la dirección IP del host y un número de puerto.

## Algunos puertos comunes y sus protocolos

* $\color{OrangeRed}{80}$: tráfico **HTTP (HyperText Transfer Protocol)** $\rightarrow$ transferencia de documentos hipertexto.
* $\color{OrangeRed}{443}$: tráfico **HTTPS (HyperText Transfer Protocol Secure)** $\rightarrow$ transferencia segura de documentos hipertexto (utiliza SSL/TLS para cifrar la comunicación).
* $\color{OrangeRed}{110}$: conexiones **POP3 (Post Office Protocol versión 3)** $\rightarrow$ recibir correos desde un servidor de correo electrónico.
* $\color{OrangeRed}{21}$: conexiones **FTP (File Transfer Protocol)** $\rightarrow$ tranferir archivos desde entre un servidor FTP y un cliente.
* $\color{OrangeRed}{22}$: conexiones **SSH (Secure Shell)** $\rightarrow$ permite conectarse de forma segura a un servidor remoto y administrar el sistema a través de una línea de comando.
* $\color{OrangeRed}{25}$: conexiones **SMTP (Simple Mail Transfer Protocol)** $\rightarrow$ enviar correos desde un servidor de correo electrónico a otro servidor de correo electrónico.
* $\color{OrangeRed}{3389}$: conexiones de Escritorio Remoto de Windows $\rightarrow$ permite comunicarse de manera remota a un sistema Windows y controlarlo como si estuviera sentado frente a el.

# Api (Interfaz de Programación de Aplicaciones)

1. Sirven como puentes que permiten que aplicaciones distintas compartan datos y funcionalidades de manera estructurada y eficiente.
2. Se trata de un conjunto de definiciones y protocolos que se utilizan para desarrollar e integrar el software de las aplicaciones, permitiendo la comunicación entre dos aplicaciones de software a través de un conjunto de reglas.

Cuando desarrollamos una API, es importante dejar documentadas las posibles respuestas para que otro desarrollador pueda utilizar nuestra API sin problemas.
* **SWAGGER**: reglas, especificaciones y herramientas que ayudan a documentar una API.

# HTTP (HyperText Transfer Protocol)

Es un protocolo de la capa de aplicación encargado de la tranferencia de documentos hipertexto.

* Usa modelo cliente-servidor.
* Utiliza TCP
    * Cliente inicia conexión TCP (crea socket) al servidor, sobre el puerto 80 (puede ser otro).
    * Servidor acepta conexión TCP del cliente.
    * Mensajes HTTP son intercambiados entre el browser y el servidor WEB.
    * Se cierra la conexión TCP.
* HTTP no guarda estado.

> [!NOTE]
> Un **socket** es un concepto abstracto por el cual dos procesos (posiblemente situados en computadoras distintas) pueden intercambiar cualquier flujo de datos, generalmente de manera fiable y ordenada.
>
>> "Es la puerta de entrada a la transmisión y recepción de datos entre dispositivos"
>
> La comunicación a través de sockets sigue un modelo cliente-servidor, donde un extremo actúa como el servidor que espera conexiones entrantes y el otro como el cliente que inicia la conexión:
> 1. El proceso comienza con la **creación** de un socket en ambas extremidades, el cliente y el servidor. El servidor escucha en un puerto específico, esperando solicitudes entrantes, mientras que el cliente especifica la dirección IP y el puerto al que desea conectarse.
> 2. El cliente inicia una solicitud de **conexión** al servidor mediante la dirección IP y el puerto. Si el servidor está disponible y acepta la conexión, se establece una conexión entre los dos extremos.
> 3. Una vez establecida la conexión, los sockets permiten la **transferencia de datos** en ambas direcciones.
> 4. Cuando la transferencia de datos ha concluido, ambas partes concluyen el **cierre la conexión**.

## Conexiones HTTP

<table>
    <tr>
        <th>HTTP no persistente</th>
        <th colspan="2">HTTP persistente</th>
    </tr>
    <tr>
        <td>Un objeto es enviado por cada conexión TCP</td>
        <td colspan="2">Múltiples objetos pueden ser enviados por una única conexión TCP entre cliente y servidor</td>
    </tr>
    <tr>
        <td align="center"><img src="./img/http_no_persistente.jpg" width="200px"/></td>
        <td align="center" colspan="2"><img src="./img/http_persistente.jpg" width="200px"/></td>
    </tr>
    <tr>
        <td rowspan="3"></td>
        <td align="center"><strong>Persistencia sin pipeline</strong></td>
        <td align="center"><strong>Persistencia con pipeline</strong></td>
    </tr>
    <tr>
        <td>El cliente envía un nuevo requerimiento sólo cuando el previo ha sido recibido</td>
        <td>El cliente envía requerimientos tan pronto éste encuentra un objeto referenciado</td>
    </tr>
    <tr>
        <td align="center"><img src="./img/no_pipelining.jpg" width="200px"/></td>
        <td align="center"><img src="./img/pipelining.jpg" width="200px"/></td>
    </tr>
</table>

<table>
    <tr>
        <td align="center">
            <strong>Round-Trip Time (RTT)</strong><br>
            The time it takes to get a response after you initiate a network request.
        </td>
        <td align="center" rowspan="2"><img src="./img/round_trip_time.jpg" width="300px"/></td>
    </tr>
    <tr>
        <td>
            <strong>Tiempo de respuesta</strong>:<br>
            - Un RTT para iniciar la conexión.<br>
            - Un RTT por requerimiento HTTP y primeros bytes de respuesta<br>
            - Tiempo de transmisión del archivo<br>
            <strong>Total</strong>: 2RTT + tiempo de transmisión.
        </td>
    </tr>
</table>

## Mensajes HTTP de respuesta

```
--------------------------------------------------------
|                Línea de Estado (Status Line)          |
--------------------------------------------------------
| HTTP/1.1 200 OK                                       |
--------------------------------------------------------

--------------------------------------------------------
|               Encabezados de Respuesta (Headers)      |
--------------------------------------------------------
| Date: Sat, 03 Aug 2024 12:34:56 GMT                   |
| Content-Type: text/html; charset=UTF-8                |
| Content-Length: 137                                   |
--------------------------------------------------------

--------------------------------------------------------
|                  Cuerpo del Mensaje (Body)            |
--------------------------------------------------------
| <!DOCTYPE html>                                       |
| <html lang="en">                                      |
| <head>                                                |
|     <meta charset="UTF-8">                            |
|     <title>Example</title>                            |
| </head>                                               |
| <body>                                                |
|     <h1>Hello, World!</h1>                            |
| </body>                                               |
| </html>                                               |
--------------------------------------------------------
```

## Códigos HTTP de respuesta

* **1xx**: Respuesta informativa $\rightarrow$ Petición recibida, continuando proceso.

> **101 Switching Protocol** $\rightarrow$ Este código se envía en respuesta a un encabezado de solicitud Upgrade por el cliente. Indica que el servidor acepta el cambio de protocolo propuesto por el usuario.

* **2xx**: Respuestas satisfactorias $\rightarrow$ Indica que la petición fue recibida correctamente, entendida y aceptada.

> **200 OK** $\rightarrow$ Request exitoso, objeto requerido es incluido en el cuerpo del mensaje.

* **3xx**: Redirecciones $\rightarrow$ El cliente tiene que tomar una acción adicional para completar la petición.

> **301 Moved Permanently** $\rightarrow$ Se movió el objeto requerido, nueva ubicación es especificada luego en el mensaje (Location:).

* **4xx**: Errores del cliente $\rightarrow$ La solicitud contiene sintaxis incorrecta o no puede procesarse.

> **404 Not Found** $\rightarrow$ Documento no encontrado en el servidor. 

* **5xx**: Errores del servidor $\rightarrow$ El servidor falló al completar una solicitud aparentemente válida.

> **505 HTTP Version Not Supported** $\rightarrow$ El servidor no soporta la versión del protocolo HTTP utilizada en la petición del navegador.

# Manejo de certificados

1. El **navegador solicita una conexión** segura al servidor del sitio web.
2. El servidor **envía su certificado emitido por una autoridad de certificación (CA)**. Este incluye la clave pública del servidor y la firma de la autoridad.
3. El **navegador verifica la autenticidad del certificado** asegurándose de que está firmado por una CA de confianza, y que el mismo no haya expirado o haya sido revocado.

* **¿Cómo se verifica?**

    1. El navegador verifica si el certificado forma parte de una cadena de confianza que conecta con una CA raíz almacenada en su lista de CAs de confianza.
    2. El navegador utiliza la clave pública de la CA para descifrar la firma digital del certificado del servidor. Si el resultado coincide con el hash del contenido del certificado, confirma que la firma es válida y que el certificado no ha sido alterado.
    3. El navegador comprueba la fecha de expiración del certificado y que el certificado sigue siendo válido.

4. Una vez verificado, **el navegador y el servidor establecen una conexión segura**. Negocian una clave de sesión cifrada que se usa para encriptar todos los datos transferidos durante la sesión.

> [!NOTE]
> Con respecto a la **cadena de confianza**: el certificado del servidor está firmado por una CA intermedia, y esta CA intermedia puede estar firmada por otra CA intermedia, hasta que finalmente se llega a una CA raíz.
> 
> ```
> [ Certificado del Servidor (www.ejemplo.com) ]
>            |
>            v
> [ Certificado de CA Intermedia ]
>            |
>            v
> [ Certificado de CA Raíz ]
>            |
>            v
> [Navegador: CA Raíz está en la lista de confianza]
> ```

# Web cache

Es un sistema que se encarga de almacenar localmente datos ya solicitados y así poder acceder a éstos más rápidamente en el futuro.

* Se clasifica como un tipo de proxy de caché.
* Almacena las respuestas de las solicitudes web.
* Puede ser instalado en diferentes niveles, como a nivel cliente, a nivel de red, o a nivel de servidor.
* Reduce el tráfico en el enlace de acceso al ISP.

**Funcionamiento:**

1. El browser envía todos los requerimientos HTTP al cache. 
2. Si el objeto está en el cache, cache retorna el objeto. 
3. En caso de no tener el objeto, cache solicita el objeto al servidor web, lo almacena y lo retorna al cliente.

> [!CAUTION]
> Un problema que puede tener un web cache mal configurado es la obsolencia que pueden tener los datos locales.

# Extras

### netstat (Network Statistic)

Provee de una lista de puertos abiertos y en uso, conexiones activas, estadísticas, etc.

* En Linux
    * netstat -t  para ver conexiones TCP.
    * netstat -u para ver conexiones UDP.

* netstat -h indica todas las opciones disponibles

* En Windows
    * netstat -p tcp  para ver conexiones TCP.
    * netstat -p udp para ver conexiones UDP.

# Webgrafía

https://es.wikipedia.org/wiki/Socket_de_Internet
https://keepcoding.io/blog/que-es-un-socket/