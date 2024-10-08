
**1. Direcciones IP: Explicá la diferencia entre una dirección IPv4 y una dirección IPv6. ¿Cuáles son las principales ventajas de IPv6 sobre IPv4? Además, proporcioná un ejemplo de cada tipo de dirección y describí su estructura.**

**Diferencia:**
- **IPv4:** Utiliza direcciones de 32 bits, lo que permite aproximadamente 4.3 mil millones de direcciones únicas. Ejemplo: `192.168.0.1`
- **IPv6:** Utiliza direcciones de 128 bits, lo que permite un número prácticamente ilimitado de direcciones (aproximadamente 3.4 × 10^38). Ejemplo: `2001:0db8:85a3:0000:0000:8a2e:0370:7334`

**Ventajas de IPv6:**
- **Capacidad:** IPv6 ofrece una cantidad mucho mayor de direcciones IP, lo que es crucial para el crecimiento continuo de Internet.
- **Configuración automática:** IPv6 facilita la autoconfiguración de dispositivos en una red.
- **Seguridad:** IPv6 tiene IPsec incorporado, proporcionando mejor seguridad.
- **Eliminación del NAT:** No es necesario utilizar traducción de direcciones de red (NAT), simplificando la conectividad.

**Estructura:**
- **IPv4:** 4 octetos separados por puntos (cada octeto es un número decimal de 0 a 255).
- **IPv6:** 8 grupos de 4 dígitos hexadecimales separados por dos puntos.


**2. DNS (Sistema de Nombres de Dominio): Describí cómo funciona el Sistema de Nombres de Dominio (DNS) y su estructura de registro. ¿Cuál es el propósito de un servidor DNS? Explicá el proceso de resolución de nombres de dominio desde que un usuario ingresa una URL en su navegador hasta que la página web es cargada.**

**Funcionamiento y propósito:**
- DNS es un sistema que traduce nombres de dominio legibles por humanos (como `www.ejemplo.com`) en direcciones IP que las computadoras utilizan para identificar servidores en la red.
- **Estructura de registro:** Los registros DNS contienen información sobre un dominio y están clasificados en varios tipos como `A`, `MX`, `CNAME`, etc.
- **Servidor DNS:** Su propósito es resolver nombres de dominio a direcciones IP para que los usuarios puedan acceder a sitios web sin memorizar direcciones IP.

**Proceso de resolución:**
1. El usuario ingresa una URL en el navegador.
2. El navegador consulta su caché DNS local. Si no encuentra la dirección IP, contacta a un servidor DNS recursivo.
3. El servidor DNS recursivo consulta otros servidores DNS (si es necesario), comenzando por el servidor raíz, luego el servidor TLD y finalmente el servidor autoritativo del dominio.
4. La dirección IP asociada al dominio se devuelve al navegador.
5. El navegador utiliza la dirección IP para establecer una conexión con el servidor web y cargar la página.


**3. VLSM (Variable Length Subnet Masking): Explicá qué es VLSM y cómo se utiliza en la creación de subredes. Proporcioná un ejemplo detallado -una red simple con dos subredes- de cómo se puede dividir una red principal en subredes utilizando VLSM, incluyendo el cálculo de las subredes y sus respectivas máscaras de subred.**

**VLSM:**
- VLSM permite subdividir una red en subredes de diferente tamaño, utilizando máscaras de subred de longitud variable, optimizando el uso de direcciones IP.

**Ejemplo:**
- Supongamos que tenemos una red `192.168.1.0/24` y necesitamos crear dos subredes: una para 100 hosts y otra para 50 hosts.
- **Primera subred (100 hosts):** La máscara de subred más cercana es `/25` (255.255.255.128), lo que permite 126 hosts.
  - Subred: `192.168.1.0/25` (Rango: `192.168.1.1 - 192.168.1.126`)
- **Segunda subred (50 hosts):** La máscara de subred adecuada es `/26` (255.255.255.192), lo que permite 62 hosts.
  - Subred: `192.168.1.128/26` (Rango: `192.168.1.129 - 192.168.1.190`)


**4. TCP/IP: Un proceso accesible en la Internet (por ejemplo, un web server) puede ser accedido conociendo la dirección IP del equipo donde se está ejecutando. Explicá detalladamente este razonamiento.**

- **Acceso mediante IP:** Si conoces la dirección IP de un servidor que ejecuta un servicio (como un servidor web), puedes acceder a ese servicio directamente ingresando la IP en tu navegador o cliente.
- **Proceso:** Cuando ingresas la IP en el navegador, se envía una solicitud HTTP o HTTPS al servidor que responde con el contenido solicitado (página web).
- **Razonamiento:** El protocolo TCP/IP es la base de Internet, y permite la transmisión de datos entre dispositivos, utilizando direcciones IP para identificar los destinos.


**5. DHCP (Protocolo de Configuración Dinámica de Host): Explicá qué es DHCP y cómo funciona. ¿Cuáles son las ventajas de usar DHCP en una red en comparación con la asignación manual de direcciones IP? Además, describe el proceso de asignación de una dirección IP a un dispositivo en una red utilizando DHCP, detallando los diferentes mensajes intercambiados durante este proceso.**

**DHCP:**
- DHCP es un protocolo que asigna automáticamente direcciones IP a dispositivos en una red, facilitando la configuración de red sin intervención manual.

**Ventajas:**
- **Automatización:** Asigna direcciones IP automáticamente, reduciendo errores y tiempo.
- **Escalabilidad:** Facilita la gestión de grandes redes.
- **Flexibilidad:** Los dispositivos pueden moverse entre redes sin problemas.

**Proceso de asignación:**
1. **Discover:** El dispositivo envía un mensaje DHCP Discover en la red para encontrar un servidor DHCP.
2. **Offer:** El servidor DHCP responde con un mensaje DHCP Offer, ofreciendo una dirección IP.
3. **Request:** El dispositivo solicita la dirección IP ofrecida enviando un mensaje DHCP Request.
4. **Ack:** El servidor DHCP confirma la asignación de la dirección IP con un mensaje DHCP Ack.

---