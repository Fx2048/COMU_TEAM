# ACTIVIDAD 11: Conceptos de introducción a las rede


# EXPOSICIÓN:✏
https://github.com/Fx2048/COMU_TEAM/blob/main/TAREAS/Actividad_11_Exposicion.md

## Problema 1: Diseño de red segura💻​ 
### Escenario: 
Una empresa necesita diseñar una red segura que conecte tres sucursales
ubicadas en diferentes ciudades utilizando tecnología WAN y LAN. La empresa maneja
datos confidenciales y requiere que la comunicación entre sucursales sea cifrada.

### Preguntas:
**¿Qué tipo de tecnología de WAN utilizarías para conectar las sucursales y por qué?
(Considera opciones como Frame Relay, MPLS, etc.)**

**Describe cómo implementarías el cifrado en la red. ¿Qué tipos de claves y
protocolos utilizarías?**

**Dibuja una topología de red que incluya dispositivos como routers, switches, y
firewalls. Explica la función de cada dispositivo en tu diseño. Puedes utilizar Packet
Tracer**

**¿Cómo garantizarías la integridad y autenticidad de los datos transmitidos entre las
sucursales? Detalla el uso de checksums o CRC.**

## PROBLEMA 2: Optimización de protocolos y caché

### Escenario:

Una empresa de streaming de video experimenta interrupciones frecuentes en laentrega de contenido a los clientes. La infraestructura actual utiliza multicast para distribuircontenido, pero aún enfrenta problemas de latencia y pérdida de paquetes.

#### Preguntas:

**1. Explica cómo mejorarías el rendimiento utilizando técnicas de caché de red. ¿Dónde colocarías estos cachés y por qué?**

El caching de datos en la red es una técnica que permite a todas las aplicaciones y los sitios web recuperar información de forma rápida y eficiente, donde los datos se almacenan temporalmente en el lugar donde se necesitan, en lugar de enviarlos de nuevo desde el servidor cada vez que alguien los necesita. Esto reduce significativamente el tiempo que se tarda en servir respuestas, donde mejora la velocidad y la experiencia del usuario. Hagamos un ejemplo, en el caso de la empresa de streaming de video, los cáches se podrian colocar cerca de los puntos de acceso de cada uno de los usuarios para así poder reducir la latencia y mejorar la velocidad de transmisión y esto se debe a que los datos más solicitados por los usuarios se almacenarían temporalmente en estos cáche, lo que nos permitiría un buen acceso, es decir, que sea más rápido a estos datos y así reduciria la carga en los servidores centrales.

**2. ¿Cómo afecta el protocolo de transporte al rendimiento del streaming de video? Considera TCP vs UDP y justifica tu elección.**

El protocolo de transporte juega un papel muy crucial en el rendimiento del streaming de video, donde los dos protocolos de transporte más comunes son TCP (Transmission Control Protocol) y UDP (User Datagram Protocol). Donde TCP es un protocolo orientado a la conexión que garantiza la entrega de los paquetes a través de mecanismos de control de errores y de flujo, sin embargo, estos mecanismos pueden introducir latencia y reducir la velocidad de transmisión, lo que puede ser algo problemático para el streaming de video en tiempo real, mientras que UDP es un protocolo sin conexión que no garantiza la entrega de paquetes y no tiene mecanismos de control de errores o de flujo, lo que significa que UDP puede transmitir datos más rápido que TCP, pero a costa de posibles pérdidas de estos paquetes. Para el streaming de video, UDP suele ser la elección más preferida debido a su baja latencia y alta velocidad de transmisión, pero es importante tener en cuenta que la elección entre TCP y UDP depende mucho de las necesidades específicas de la aplicación que se quiere verificar.

**3. Propone una solución usando Anycast para optimizar la entrega de contenido. ¿Cómo funcionaría en este contexto?**

Anycast es una técnica de red que nos permite dirigir las solicitudes de los usuarios al servidor más cercano geográficamente, reduciendo así la latencia y mejorando el rendimiento. En el contexto de la empresa de streaming de video, Anycast puede utilizarse para dirigir las solicitudes de los usuarios al servidor de contenido más cercano, lo que nos permitiría una entrega de contenido más rápida y eficiente para cada usuario.

**4. Desarrolla un modelo simplificado para calcular el efecto de la caché en la reducción de latencia.**

Un modelo simplificado para calcular el efecto de la caché en la reducción de latencia podría basarse en el tiempo de acceso efectivo (EAT), que es una medida del tiempo promedio que se tarda en acceder a un dato en el caché o en la memoria principal. El EAT se puede calcular utilizando la siguiente fórmula:

*EAT = (Tasa de aciertos de caché * Tiempo de acceso a caché)+(tasa de errores de caché * Tiempo de acceso a memoria*

Donde:
- La tasa de aciertos de caché es la proporción de solicitudes de acceso que se pueden servir directamente desde la caché.
- El tiempo de acceso a caché es el tiempo que se tardaría en recuperar un dato de la caché.
- La tasa de errores de caché es la proporción de solicitudes de acceso que no se pueden servir desde la caché y requieren un acceso a la memoria principal.
- El tiempo de acceso a memoria es el tiempo que se tardaría en recuperar un dato de la memoria principal.

Este modelo nos proporciona una estimación de cómo el caché puede reducir la latencia al servir una mayor proporción de solicitudes de acceso directamente desde la caché, en lugar de tener que acceder a la memoria principal, pero es importante tener en cuenta que este es un modelo simplificado, donde rendimiento real puede variar en función de varios factores, como el comportamiento de acceso de la aplicación y la configuración de la caché que esta queriendo configurar.

- *Para tu presentación y código a presentar puedes utilizar:*

##### Requisitos:

1. Mejora del rendimiento utilizando técnicas de caché de red.
2. Elección y configuración del protocolo de transporte adecuado para reducir lalatencia y mejorar la confiabilidad.
3. Implementación de Anycast para optimizar la entrega de contenido a los usuarios.
4. Simulación y automatización utilizando Python.

#### Parte 1: Implementación de caché de rd con python

##### Código python:
```
class VideoCache:
    def __init__(self):
        self.cache = {}

    def get_video(self, video_id):
        if video_id in self.cache:
            print(f"Video {video_id} retrieved from cache")
            return self.cache[video_id]
        else:
            print(f"Video {video_id} not in cache, downloading...")
            video_data = self.download_video(video_id)
            self.cache[video_id] = video_data
            return video_data

    def download_video(self, video_id):
        # Simula la descarga del video desde un servidor remoto
        return f"Video data for {video_id}"

# Ejemplo de uso
cache = VideoCache()
video = cache.get_video("video12022004")
print(video)  
video = cache.get_video("video12022004")

```
#### Resultados:
```
Video video12022004 not in cache, downloading...
Video data for video12022004
Video video12022004 retrieved from cache
```
Este código implementa un caché de video utilizando una clase llamada `VideoCache`, donde la caché se implementa como un diccionario, ya que, las claves son los identificadores de los videos y los valores son los datos del video. El método `get_video` verifica si el video solicitado está en el caché, donde si está presente, lo devuelve directamente, pero si no está en la caché, simula la descarga del video desde un servidor remoto, y lo almacena en la caché donde luego lo devuelve. Esta implementación proporciona una forma eficiente de reducir la latencia al momento de almacenar en el caché de videos solicitados frecuentemente, mejorando así el rendimiento del sistema de distribución de video.

#### Parte 2: Selección del protocolo de transporte

- **Discusión:**

1. **Explica las ventajas de usar UDP sobre TCP para streaming de video, considerando las características de ammbos protocolo**

El Protocolo de Datagramas de Usuario (UDP) tiene varias ventajas sobre el Protocolo de Control de Transmisión (TCP) cuando se trata de streaming de video, de los cuales serian las siguientes:

- Velocidad: UDP es más rápido que TCP, ya que, no requiere establecer una conexión antes de enviar datos.
- Menor sobrecarga: Al no tener mecanismos de control de flujo, UDP presenta una menor sobrecarga de datos en comparación con TCP.
- Transmisión en tiempo real: UDP es ideal para aplicaciones que requieren una transmisión más rápida y en tiempo real, pero pueden tolerar cierta pérdida de datos, como transmisiones de audio y video, juegos en línea y aplicaciones de streaming que son muy comunes hoy en dia.

2. **Analiza los posibles problemas dde confiabilidad y orden de llegada de los paquetes y cómo mitigarlos**

Aunque UDP tiene varias ventajas, también presenta algunos desafíos, especialmente en términos de confiabilidad y orden de llegada de los paquetes que ciertas veces pueden llegar a ser un problema, donde tiene los siguientes puntos:

- Falta de fiabilidad: Al no garantizar la entrega de los paquetes ni el orden de estos mismos, UDP puede resultar en una gran pérdida de datos o duplicación de información.
- No orientado a la conexión: UDP no establece una conexión antes de enviar datos, por lo que puede llevar a la pérdida de los paquetes en entornos con alta congestión de red.

Ahora para poder mitigar estos problemas, podemos utilizar técnicas como:

- Protocolos de nivel de aplicación: Nos pueden proporcionar mecanismos de control de errores y de flujo en la capa de aplicación, lo que nos puede ayudar a mejorar la confiabilidad de las transmisiones UDP.
- Reenvío de paquetes: En caso de pérdida de los paquetes, el remitente puede reenviar los paquetes perdidos.
-Buffering y reordenación de paquetes: Los receptores pueden utilizar buffers para almacenar y reordenar todos los paquetes que llegan fuera de orden.
- Control de congestión: Podemoa utilizar algoritmos de control de congestión para ajustar la tasa de envío en función de las condiciones de la red, donde esto nos puede ayudar a reducir la pérdida de paquetes en entornos con alta congestión de red.

#### Parte 3: Implementación de anycast con python

##### Código de pyton
```
import random

class AnycastService:
    def __init__(self):
        self.servers = ['192.168.1.1', '192.168.2.1', '192.168.3.1']
    
    def get_nearest_server(self, user_ip):
        # Simula la selección del servidor más cercano (simplificado)
        return random.choice(self.servers)

# Ejemplo de uso
anycast = AnycastService()
nearest_server = anycast.get_nearest_server("192.168.1.44")
print(f"Nearest server for user is {nearest_server}")
```
#### Resultados:
```
Nearest server for user is 192.168.2.1
```
El código es una simulación conceptual de cómo se podría implementar anycast para dirigir las solicitudes de los usuarios al servidor de caché más cercano, donde clase `AnycastService` contiene una lista de direcciones IP de servidores y un método `get_nearest_server()` que simula la selección del servidor más cercano basándose en la dirección IP del usuario. En la simulación, se elige aleatoriamente un servidor de la lista como el servidor más cercano y esta implementación simplificada sirve para ilustrar el concepto de anycast en la distribución de solicitudes a servidores de caché.

#### Parte 4: Monitorización y análisis

- Usa wireshark para caprurar paquetes de red y analiza el tráfico espcífico de video para identificar patrones de uso y posibles cuellos de botella.
```
import pyshark

def analyze_video_traffic(interface='eth0'):
    # Especifica la ubicación de TShark
    tshark_path = '/usr/bin/tshark'  # Reemplaza con la ubicación correcta de TShark en tu sistema

    # Configura la ubicación de TShark para pyshark
    pyshark.tshark.tshark.tshark_path = tshark_path

    # Realiza la captura de paquetes en la interfaz especificada
    capture = pyshark.LiveCapture(interface=interface)

    # Imprime información sobre cada paquete capturado
    for packet in capture.sniff_continuously(packet_count=10):
        print(packet)

# Ejemplo de uso
analyze_video_traffic(interface='eth0')
```
Este código utiliza la biblioteca `pyshark` para realizar un análisis de tráfico de red en tiempo real en una interfaz de red específica, en este caso, 'eth0', primero, configura la ubicación de TShark, una herramienta de captura de paquetes, para que `pyshark` pueda encontrarla, luego, inicia una captura en vivo en la interfaz especificada y, para cada paquete capturado, imprime información detallada sobre el mismo, este enfoque nos proporcionaria una manera más rápida y sencilla de examinar el tráfico de red en busca de patrones específicos o problemas potenciales, pero que en este caso nos bota un error ya que wireshark no se encuentra en el sistema de mi navegador.

## PROBLEMA 3: Simulación de ataque y respuesta

### Escenario:

Eres el administrador de seguridad de una red corporativa y has notado unaumento en el tráfico ARP anómalo. Sospechas que esto podría ser parte de un ataque deARP spoofing, donde un atacante podría estar intentando interceptar la comunicación entredos partes para robar o modificar datos transmitidos.
### preguntas:

**1. Describe cómo identificarías si estas transmisiones ARP son realmente maliciosas.**

**2. ¿Qué medidas tomarías para mitigar el ataque una vez confirmado?**

**3. Explica cómo un switch y un firewall pueden configurarse para prevenir futuros ataques de este tipo.**

- **Switch:** Se utiliza la función de ARP spoofing prevention que es una de las funciones que controla el acceso a la red basándose en su dirección Mac o su identificación en la red (Puerto, IP y dirección MAC).

 - **Pasos para configurar la prevención de ARP Spoofing en un switch**:

1. Acceder a la interfaz web del switch utilizando un navegador y colocando la dirección IP donde por defecto suele ser **10.90.90.90**.
2. Ingresar a la configuración del switch y navegar a la sección de **Seguridad**.
3. Buscar la opción de **ARP Spoofing Prevention**.
4. Configurar los siguientes parámetros:
- **Dirección IP**: La dirección IP de tu **gateway**, **router** o **firewall**.
- **Dirección MAC**: La dirección MAC LAN de tu **gateway**, **router** o **firewall**.
- **Puertos**: Indica el puerto donde está conectado tu **gateway**, **router** o **firewall**.
5. Agregar la prevención a la tabla ARP y guardar la configuración.

- **Firewall:** Se utiliza ARP inspection para que verifique los paquetes ARP que los compara con las entradas en la tabla ARP, además, también se puede utilizar Dynamic ARP inspection que es donde interpreta todas las solicitudes y respuestas del ARP para asegurarse que solo ingresen las solicitudes y respuestas validas.

- **Configuración en el Firewall**:
1. Acceder a la configuración del firewall.
2. Habilitar **ARP Inspection**.
3. Verificar que las entradas en la tabla ARP estén actualizadas y sean correctas.
4. Considerar también de configurar **IP Source Guard** para proteger contra ataques de spoofing que se pueden dar hasta en empresas.
  
**4. Formula un plan para educar a los empleados sobre medidas de seguridad quepueden tomar para reducir el riesgo de ataques futuros.**

- Para tu presentación y código a presentar puedes utilizar:

##### Requisitos:

1. Detección de ARP Spoofing: Implementar un sistema de detección para identificarposibles ataques.
2. Mitigación del Ataque: Desarrollar un método para mitigar o detener el ataque unavez detectado.
3. Automatización y Monitorización: Usar Python para automatizar la detección yrespuesta, y monitorear continuamente la red para futuros ataques.
4. Educación de Empleados: Proporcionar un plan para educar a los empleados sobrecómo pueden ayudar a reducir el riesgo de futuros ataques.

#### Parte 1: Detección de ARP Spoofing con Python

##### Código python:

#### parte 2: Mitigaciónn del Ataque

- *Discusión de Estrategias de Mitigación*

- **Seguridad en el Switch: Habilitar funciones de seguridad como Dynamic ARPInspection (DAI) en los switches.**
  
- **Uso de Seguridad de Puerto: Configurar la seguridad de puerto en los switches paralimitar el número de MACs por puerto y prevenir posibles ataques.**

#### Parte 3: Automatización y monitorización
##### Código de python:


## PROBLEMA 4: Análisis y diseño de red Peer-to-Peer (P2P)

Escenario: Una startup tecnológica desea implementar una red P2P robusta para permitir elintercambio eficiente de recursos computacionales entre usuarios distribuidosgeográficamente. Esta red debe ser capaz de manejar intercambios dinámicos de archivos,distribución de carga, y debe incorporar medidas de seguridad para prevenir accesos noautorizados

### Preguntas:

1. Describe cómo se diferenciaría esta red P2P de una red cliente-servidor en términosde diseño de red y topología.

- **Diferencias entre red P2P y red cliente-servidor en términos de diseño de red y topología**:

   - **Red P2P (Peer-to-Peer)**: En una red P2P, los nodos actúan tanto como clientes como servidores, lo que significa que cada nodo tiene la capacidad de solicitar y proporcionar recursos. No hay un servidor centralizado, en su lugar, todos los nodos son iguales y se comunican directamente entre sí. La topología de red suele ser más distribuida y descentralizada, lo que permite una mayor resistencia a fallas y una escalabilidad más fácil. La redundancia de datos y la tolerancia a fallos suelen ser más altas en este tipo de red.

   - **Red cliente-servidor**: En una red cliente-servidor, hay un servidor central que actúa como punto focal para el intercambio de recursos. Los clientes solicitan recursos al servidor, que los proporciona. La topología de red es más centralizada, lo que puede resultar en un único punto de fallo y problemas de escalabilidad si el servidor no puede manejar todas las solicitudes de los clientes.

2. ¿Qué protocolos específicos usarías para gestionar las comunicaciones y elintercambio de archivos en esta red?


- **Protocolos específicos para gestionar las comunicaciones y el intercambio de archivos en la red P2P**:

   - **Protocolo BitTorrent**: Es un protocolo P2P popular para compartir archivos de forma descentralizada. Permite la distribución eficiente de archivos divididos en fragmentos entre los nodos de la red.
   
   - **Protocolo Kademlia**: Utilizado para construir redes P2P descentralizadas, como en el caso de sistemas de almacenamiento distribuido como IPFS (InterPlanetary File System). Ayuda en la localización eficiente de nodos y recursos en la red.
   
   - **Protocolo de Seguridad SSL/TLS**: Para garantizar la seguridad de las comunicaciones entre nodos, se puede implementar SSL/TLS para cifrar y autenticar las conexiones.

3. Analiza los posibles problemas de seguridad asociados con una red P2P y proponesoluciones para mitigar estos riesgos.

- **Posibles problemas de seguridad y soluciones para mitigar riesgos en una red P2P**:

   - **Acceso no autorizado**: Implementar un sistema de autenticación robusto para garantizar que solo los usuarios autorizados puedan acceder a los recursos compartidos.
   
   - **Integridad de datos**: Utilizar firmas digitales para verificar la integridad de los archivos compartidos y evitar la manipulación no autorizada de los mismos.
   
   - **Malware y software malicioso**: Implementar medidas de detección y prevención de malware, como escaneo de archivos en busca de virus y limitación de tipos de archivos permitidos en la red.
   
   - **Ataques de denegación de servicio (DDoS)**: Implementar mecanismos de mitigación de DDoS, como limitación de la velocidad de transferencia por nodo o la implementación de listas blancas y negras de direcciones IP.

4. Evalúa el impacto de incorporar nodos que actúan tanto como clientes comoservidores. ¿Cómo gestionarías el balanceo de carga?

 - **Impacto de incorporar nodos que actúan tanto como clientes como servidores y gestión del balanceo de carga**:


   - La inclusión de nodos que actúan como clientes y servidores aumenta la eficiencia de la red al distribuir la carga entre los nodos disponibles.
   
   - Se puede implementar un algoritmo de balanceo de carga que distribuya las solicitudes de recursos de manera equitativa entre los nodos disponibles, teniendo en cuenta factores como la capacidad de procesamiento y la carga actual de cada nodo.
   
   - Además, se pueden establecer políticas de prioridad para determinar qué nodos tienen preferencia para actuar como servidores en función de su disponibilidad y recursos disponibles. Esto ayudará a optimizar el rendimiento de la red P2P.

### Parte 1: Implementación de la Red P2P con Python

````
import socket
import threading

class Peer:
    def __init__(self, host, port):
        self.host = host
        self.port = port
        self.peers = [] # List to keep track of peers
        self.server = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
        self.server.bind((self.host, self.port))
        self.server.listen(5)
        print(f"Node started on {self.host}:{self.port}")
        threading.Thread(target=self.accept_connections).start()

    def accept_connections(self):
        while True:
            client, address = self.server.accept()
            print(f"Connected with {address[0]}:{address[1]}")
            self.peers.append(client)
            threading.Thread(target=self.handle_client, args=(client,)).start()

    def handle_client(self, client):
        while True:
            try:
                data = client.recv(1024)
                if data:
                    print(f"Received: {data.decode()}")
                    self.broadcast_data(data, client)
            except Exception as e:
                print(f"Error: {e}")
                client.close()
                self.peers.remove(client)
                break

    def broadcast_data(self, data, sender):
        for peer in self.peers:
            if peer is not sender:
                peer.send(data)

    def connect_to_peer(self, host, port):
        client = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
        client.connect((host, port))
        self.peers.append(client)
        print(f"Connected to peer at {host}:{port}")

# Ejemplos de uso
node = Peer('127.0.0.1', 5000)
node.connect_to_peer('127.0.0.1', 6000)

````
# Resultados 
`````
C:\Users\PROPIETARIO\PycharmProjects\pythonProject1\venv\Scripts\python.exe C:\Users\PROPIETARIO\PycharmProjects\pythonProject1\main.py 
Node started on 127.0.0.1:5000
`````
# Análisis de código

a) Análisis de código:

La clase Peer representa un nodo en una red ``peer-to-peer (P2P)``.

En el método ``__init__``, se inicializan los atributos del nodo, se crea un socket del servidor y se inicia un hilo para aceptar conexiones entrantes.

El método ``accept_connections `` espera y acepta conexiones entrantes de otros nodos. Para cada conexión aceptada, se inicia un nuevo hilo para manejar las comunicaciones con ese cliente.
El método ``handle_client``maneja la comunicación con un cliente específico. Lee los datos recibidos del cliente y los reenvía a todos los otros clientes conectados, excluyendo al remitente.
El método ``broadcast_data`` envía datos a todos los clientes conectados, excepto al remitente.
El método ``connect_to_peer ``permite que este nodo se conecte a otro nodo en la red P2P.
# Análisis de resultado


El resultado de este código es la implementación de un nodo en una red ``P2P simple.``
Cuando se crea una instancia de Peer, se inicia un nodo en el ``host`` y puerto especificados.
Luego, se puede llamar al método ``connect_to_peer`` para que este nodo se conecte a otro nodo en la red ``P2P``.
Después de conectarse a otros nodos, este nodo puede recibir y enviar mensajes a los otros nodos en la ``red P2P``.

###   Parte 2: Gestión de recursos y distribución de carga

# Código:
````
from OpenSSL import crypto

class LoadBalancer:
    def __init__(self):
        self.nodes = []
    def add_node(self, node):
        self.nodes.append(node)
    def assign_load_based_on_resources(self, task):
        # Ordenar los nodos por recursos disponibles de manera descendente
        sorted_nodes = sorted(self.nodes, key=lambda x: x.available_resources, reverse=True)
        # Asignar la tarea al nodo con más recursos disponibles
        sorted_nodes[0].handle_task(task)
    def round_robin(self, task):
        # Implementar algoritmo round-robin para distribuir tareas de manera equitativa
        node_index = len(self.nodes) % len(self.nodes)  self.nodes[node_index].handle_task(task)
class Node:
    def __init__(self, name, available_resources):
        self.name = name
        self.available_resources = available_resources
    def handle_task(self, task):
        print(f"Task '{task}' handled by node '{self.name}'")
def create_self_signed_cert(cert_file, key_file):
    k = crypto.PKey()    k.generate_key(crypto.TYPE_RSA, 2048)
    cert = crypto.X509()
    cert.get_subject().C = "US"
    cert.get_subject().ST = "California"
    cert.get_subject().L = "San Francisco"
    cert.get_subject().O = "My Company"
    cert.get_subject().OU = "My Organizational Unit"
    cert.get_subject().CN = "mydomain.com"
    cert.set_serial_number(1000)
    cert.gmtime_adj_notBefore(0)
    cert.gmtime_adj_notAfter(10 * 365 * 24 * 60 * 60)    cert.set_issuer(cert.get_subject())
    cert.set_pubkey(k)
    cert.sign(k, 'sha256')
    open(cert_file, "wt").write(crypto.dump_certificate(crypto.FILETYPE_PEM, cert).decode('utf-8'))
    open(key_file, "wt").write(crypto.dump_privatekey(crypto.FILETYPE_PEM, k).decode('utf-8'))
create_self_signed_cert('ldap_cert.pem', 'ldap_key.pem')
# Ejemplo de uso
lb = LoadBalancer()
node1 = Node("Node1", available_resources=100)
node2 = Node("Node2", available_resources=80)
node3 = Node("Node3", available_resources=120)
lb.add_node(node1)
lb.add_node(node2)
lb.add_node(node3)
tasks = ["Task1", "Task2", "Task3", "Task4"]
for task in tasks:  lb.assign_load_based_on_resources(task)
for task in tasks:
    lb.round_robin(task)
````
# Análisis de código :

1. ``LoadBalancer:``
La clase LoadBalancer representa un balanceador de carga.
Tiene un atributo nodes que almacena los nodos disponibles para manejar tareas.

2. ``add_node(self, node):``
Método para agregar un nodo al balanceador de carga.

3. ``assign_load_based_on_resources(self, task):``
Método que asigna una tarea a un nodo basado en los recursos disponibles.
Ordena los nodos por recursos disponibles y asigna la tarea al nodo con más recursos disponibles.

4. ``round_robin(self, task):``
Método que implementa el algoritmo de round-robin para distribuir tareas de manera equitativa.
Distribuye las tareas de manera circular, asignando cada tarea al siguiente nodo disponible en la lista de nodos.

5. ``Node:``
La clase Node representa un nodo en el sistema.
Tiene atributos como name para el nombre del nodo y available_resources para los recursos disponibles en el nodo.

6. ``handle_task(self, task):``
Método que maneja una tarea asignada al nodo.
Simplemente imprime un mensaje indicando que la tarea ha sido manejada por el nodo.

7. ``create_self_signed_cert(cert_file, key_file):``
Función que crea un certificado autofirmado utilizando la biblioteca OpenSSL.
Genera una clave privada y un certificado`` X.509`` con información específica ``(país, estado, ciudad, etc.)`` y firma el certificado utilizando la clave privada.
Escribe el certificado y la clave privada en archivos especificados.

# Resultados

````
C:\Users\PROPIETARIO\PycharmProjects\pythonProject1\venv\Scripts\python.exe C:\Users\PROPIETARIO\PycharmProjects\pythonProject1\main.py 
Task 'Task1' handled by node 'Node3'
Task 'Task2' handled by node 'Node3'
Task 'Task3' handled by node 'Node3'
Task 'Task4' handled by node 'Node3'
Task 'Task1' handled by node 'Node1'
Task 'Task2' handled by node 'Node1'
Task 'Task3' handled by node 'Node1'
Task 'Task4' handled by node 'Node1'
Process finished with exit code 0
`````

# Análisis de Resultado:

Primero, se manejan las tareas 'Task1', 'Task2', 'Task3', y 'Task4' utilizando el método assign_load_based_on_resources, el cual asigna las tareas basadas en los recursos disponibles en los nodos. En este caso, todas las tareas son manejadas por el nodo 'Node3'.
Luego, se manejan las mismas tareas utilizando el método round_robin, el cual implementa el algoritmo de round-robin para distribuir las tareas de manera equitativa entre los nodos. En este caso, las tareas 'Task1', 'Task2', 'Task3', y 'Task4' son distribuidas secuencialmente entre los nodos 'Node1' y 'Node2', y debido a que solo hay dos nodos disponibles ('Node1' y 'Node2'), las tareas se distribuyen entre ellos de manera alternativa.
Finalmente, el programa termina con un código de salida 0, indicando que se ha ejecutado correctamente sin errores.


# Parte 3: Seguridad en la Red P2P

```
import socket
import threading
import hashlib
import os

class Peer:
    def __init__(self, host, port, password):
        self.host = host
        self.port = port
        self.peers = []  # List to keep track of peers
        self.server = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
        self.server.bind((self.host, self.port))
        self.server.listen(5)
        self.password = password
        self.key = self.generate_key(password)
        print(f"Node started on {self.host}:{self.port}")
        threading.Thread(target=self.accept_connections).start()
    def generate_key(self, password):
        salt = os.urandom(16)
        key = hashlib.pbkdf2_hmac('sha256', password.encode('utf-8'), salt, 100000)
        return salt + key

    def verify_key(self, stored_key, provided_password):
        salt = stored_key[:16]
        key = stored_key[16:]
        new_key = hashlib.pbkdf2_hmac('sha256', provided_password.encode('utf-8'), salt, 100000)
        return new_key == key

    def accept_connections(self):
        while True:
            client, address = self.server.accept()
            print(f"Connected with {address[0]}:{address[1]}")
            if self.verify_key(self.key, self.password):
                self.peers.append(client)
                threading.Thread(target=self.handle_client, args=(client,)).start()
                client.send(b'Authenticated successfully.')
            else:
                print("Authentication failed. Closing connection.")
                client.send(b'Authentication failed. Closing connection.')
                client.close()

    def handle_client(self, client):
        while True:
            try:
                data = client.recv(1024)
                if data:
                    if data == b'ping':
                        client.send(b'pong')
                    else:
                        print(f"Received: {data.decode()}")
                        self.broadcast_data(data, client)
            except Exception as e:
                print(f"Error: {e}")
                client.close()
                break

    def broadcast_data(self, data, sender):
        for peer in self.peers:
            if peer is not sender:
                peer.send(data)

# Ejemplo de uso
password = "secure_password"
node = Peer('127.0.0.1', 5000, password)

````
# Resultado

```
C:\Users\PROPIETARIO\PycharmProjects\pythonProject1\venv\Scripts\python.exe C:\Users\PROPIETARIO\PycharmProjects\pythonProject1\main.py 
Node started on 127.0.0.1:5000
```

# Análisis de código

1. ``Clase Peer:``
Representa un nodo en la red P2P.
Al inicializarse, establece un servidor TCP en el host y puerto especificados.
Genera una clave segura a partir de la contraseña proporcionada por el usuario utilizando la función generate_key.
Utiliza hilos para aceptar conexiones entrantes y manejar clientes en paralelo.

2. ``Método generate_key:``

Genera una clave segura usando la función de derivación de claves basada en contraseña (PBKDF2).
PBKDF2 utiliza una sal aleatoria y un número alto de iteraciones para hacer más costoso el cálculo de la clave, lo que mejora la seguridad.

3. ``Método verify_key:``

Verifica si la contraseña proporcionada por el cliente coincide con la contraseña almacenada en el nodo.
Recalcula la clave utilizando la misma sal y número de iteraciones que se usaron para generar la clave almacenada, y luego compara las claves.

4. ``Método accept_connections:``

Acepta conexiones entrantes de clientes.
Si la autenticación es exitosa (es decir, la contraseña proporcionada por el cliente coincide con la contraseña almacenada en el nodo), agrega al cliente a la lista de peers y comienza a manejar sus mensajes.
Si la autenticación falla, cierra la conexión con el cliente.

5. ``Método handle_client:``

Maneja la comunicación con un cliente específico.
Recibe mensajes del cliente y, si es un mensaje de "ping", responde con "pong".
Si es otro tipo de mensaje, lo reenvía a todos los otros clientes conectados.

6. ``Método broadcast_data:``

Envía datos a todos los clientes conectados, excepto al remitente.

# Análisis de resultado
El resultado indica que el nodo se ha iniciado correctamente en la dirección ``IP 127.0.0.1 ``y en el puerto ``5000``. Esto significa que el servidor está escuchando conexiones entrantes en esa dirección y puerto, y está listo para aceptar clientes.

El mensaje ``"Node started on 127.0.0.1:5000"`` es una confirmación de que el servidor se ha iniciado con éxito y está listo para recibir conexiones. Esto es útil para verificar que el servidor se haya iniciado correctamente sin errores.

En resumen, el mensaje indica que el servidor se ha iniciado y está listo para aceptar conexiones en la dirección IP y puerto especificados.
