1. Una conexión HTTP 1.1 persistente sin pipeline es más eficiente que una HTTP 1.1 persistente con pipeline dado que la primera no requiere establecer la conexión.

Falso. Todas las conexiones HTTP 1.1 persistente requieren del establecimiento de una conexión inicial. Lo que difencia una conexión con y sin pipeline, es que en el caso de la primera, las referencias a otros recursos (objetos) en un archivo HTML son solicitados unos tras otro a medida que se los va a hallando en el HTML sin necesidad de que el recursos anterior haya sido solicitado y recibido (pueden solicitarse simultáneamente). En el segundo caso (sin pipeline), es necesario que el recurso sea solicitado al servidor y que los paquetes que contienen el mismo, sean recibidos por el solicitante. Luego de esto, es que se podrá solicitar un recurso nuevo.

2. El ISP debe ser el propietario de la red de acceso del usuario al PoP (punto de presencia).

Falso. No es exclusivamente necesario que el ISP sea propietario de la red de acceso del usuario al PoP. Pueden existir acuerdos de peering o tránsito entre distintos proveedores.

3. SMTP se considera como un protocolo que funciona de manera Pull ya que obtiene contenido desde un servidor.

Falso. El protocolo SMTP se encarga del envio de correos desde un servidor de correos (cliente) a otro servidor de correos (servidor).

4. En el protocolo DNS un registro del tipo MX tiene como parámetro name al nombre del host y como parámetro value a la dirección IP asociada a ese host.

Falso. El parámetro "name" contiene el nombre del dominio (no el de host), y el parámetro "value" contiene el nombre del servidor de correo (no la dirección IP).

Ejemplo:

* Registro MX: example.com. IN MX 10 mail.example.com.
    * name: example.com.
    * value: mail.example.com. (nombre del servidor de correo, no la dirección IP directamente)

5. ARP es usado en redes ethernet, pero no en redes wifi.

Falso. ARP (Adress Resolution Protocol) es utilizado tanto en redes Ethernet como en redes Wi-Fi para resolver direcciones IP a direcciones MAC.

6. Utilizando el utilitario “ping”, es posible conocer el tiempo de demora de los paquetes en ir de emisor a receptor y volver.

Verdadero. El comando ping se utiliza para medir el tiempo que tardan los paquetes en ir y volver entre dos dispositivos.

7. La máscara de red 255.255.128.0 puede tener 32768 redes y 131072 hosts.

Falso. La máscara de red 255.255.128.0 puede tener $2^17 = 131072$ (ya que son 17 bits de red) y $2^15 = 32768$ (ya que son 15 bits de red).

8. Una tabla de Iptables, puede incluir varias cadenas, pero solo las permitidas para esa tabla.

Verdadero. Cada tabla Iptables tiene varias cadenas asociadas a la misma. Por ejemplo, la tabla FILTER solo admite las cadenas INPUT, FORWARD, OUTPUT.

9. En las redes que usan tecnología Packet Switching, cada paquete de datos es almacenado y retransmitido siguiendo el camino (entre nodos) establecido para la conexión.

Falso. Packet Switching permite que los datos se dividan en paquetes más chicos antes de ser enviados. Cada paquete se envía de forma independiente y puede seguir distintas rutas para llegar a destino, donde se reensamblan en orden correcto.

10. Cada entrada en la tabla de ruteo debe contener (entre otros elementos) la red de destino, la interfaz por la cual ha de reenviar los datagramas y la dirección IP de esa interfaz.

Verdadero. La tabla de ruteo contiene:

* Red destino: donde se enviarán los datagramas.
* IP sig router: dirección del router a través del cual se accederá a la red destino.
* Interfaz de salida: salida que debe tomar el router para llegar al sig router o a la red destino.
* Indica si la red destino es directa o indirecta (debe pasar por un router intermedio).

11. Aproximadamente el 50% de las comunicaciones intercontinentales entre ISPs se realizan usando cables submarinos, mientras que el otro 50% se realizan usando satélites geoestacionarios.

Falso. La mayoría de las comunicaciones intercontinentales se realizan a través de cables submarinos, mientras que una pequeña parte utiliza satélites debido a la mayor latencia y menor capacidad de estos últimos.

12. 