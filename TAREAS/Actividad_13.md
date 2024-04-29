![image](https://github.com/Fx2048/COMU_TEAM/assets/131219987/950b02d6-e31e-415a-834b-75a7292bf9d2)
## PROBLEMA 1: Diseño de un sistema de entrega y recuperación de correo electrónico
### Contexto:
Una empresa necesita diseñar un sistema de correo electrónico robusto que utilice SMTP, IMAP, y SSL/TLS para la entrega y recuperación segura de correo electrónico.
#### Objetivo:
Implementaremos servidores SMTP y IMAP usando librerías en Python que simulen el comportamiento de estos protocolos.

Manejo de SSL/TLS:
Utilizaremos SSL/TLS para encriptar las conexiones SMTP e IMAP, garantizando la confidencialidad y la integridad de los datos transmitidos.

Integración con DHCP y NAT:
Discutiremos cómo las direcciones IP dinámicas asignadas por DHCP y la traducción de direcciones realizada por NAT pueden afectar la configuración y el funcionamiento de los servidores de correo.

#### Paso 1: Configuración del servidor SMTP y IMAP en Python
#### Paso 2: Implementación de SSL/TLS
#### Paso 3: Manejo de Certificados X.509
#### Paso 4: Discusión sobre DHCP y NAT

## PROBLEMA 2: Implementación de un protocolo de red personalizado sobre TCP

### Contexto: 

Diseñar un protocolo de aplicación personalizado para un sistema de archivosdistribuido que se ejecutará sobre TCP, utilizando técnicas como multiplexación y control de flujo.

- *Para tu presentación y código a presentar puedes utilizar:*

##### Objetivos:

1. Diseño del protocolo: Definir el formato del mensaje, incluidas las cabeceras y lasextensiones de cabecera para manejar funcionalidades específicas como control deflujo y recuperación de errores.
2. Implementación de control de flujo: Desarrollar un esquema de control de flujo paramanejar eficazmente la transferencia de datos sobre TCP.
3. Simulación con Python: Simular el protocolo utilizando Python para evaluar surendimiento y robustez en escenarios de red simulados.

#### Paso 1: Diseño del protocolo

Vamos a definir un protocolo simple que incluya operaciones básicas como PUT, GET, yDELETE para interactuar con archivos en el sistema distribuido.

- Ejemplo de Especificación del Protocolo:

● PUT: Enviar un archivo al sistema.

● GET: Recuperar un archivo del sistema.

● DELETE: Eliminar un archivo del sistema.

Cada mensaje tendrá una cabecera que incluye el tipo de operación, el tamaño del mensaje, y un número de secuencia para el control de flujo y la recuperación de errores
#### Código en python:
```
class ProtocolMessage:
    def __init__(self, operation, message_size, sequence_number):
        self.operation = operation  # Tipo de operación (PUT, GET, DELETE)
        self.message_size = message_size  # Tamaño del mensaje
        self.sequence_number = sequence_number  # Número de secuencia para control de flujo

class FileTransferProtocol:
    def __init__(self):
        self.sequence_number = 0  # Inicializar el número de secuencia
    
    def send_request(self, operation, file_data=None):
        if operation == "PUT":
            message_size = len(file_data) if file_data else 0
            self.sequence_number += 1
            request = ProtocolMessage(operation="PUT", message_size=message_size, sequence_number=self.sequence_number)
        elif operation in ["GET", "DELETE"]:
            request = ProtocolMessage(operation=operation, message_size=0, sequence_number=self.sequence_number)
        else:
            print("Invalid operation")
            return
        
        # Simulación de envío del mensaje
        print(f"Sending {operation} request: Operation={request.operation}, Size={request.message_size}, Sequence Number={request.sequence_number}")


protocol = FileTransferProtocol()
protocol.send_request("PUT", file_data="file_content")
protocol.send_request("GET")
protocol.send_request("DELETE")

```
#### Resultados:
```
Sending PUT request: Operation=PUT, Size=12, Sequence Number=1
Sending GET request: Operation=GET, Size=0, Sequence Number=1
Sending DELETE request: Operation=DELETE, Size=0, Sequence Number=1
```
Este código crea una clase `ProtocolMessage` que contiene la información requerida para cada mensaje del protocolo,donde la clase `FileTransferProtocol` incluye un método `send_request` que permite enviar solicitudes PUT, GET y DELETE, creando un objeto `ProtocolMessage` correspondiente para cada operación. Se simula el envío del mensaje imprimiendo los detalles de la solicitud en la consola, además, de haber añadido un número de secuencia que se incrementa con cada solicitud para el control de flujo en el sistema.

#### Paso 2: Implementación de control de flujo

##### Código Python para simulación del protocolo:

#### Paso 3: Evaluación del protocolo

- Después de implementar el protocolo, usaríamos herramientas como Wireshark paramonitorear la eficacia del control de flujo y el manejo de errores durante la transferencia dearchivos. Esto podría involucrar la simulación de condiciones de red adversas, como altalatencia y pérdida de paquetes, para ver cómo el protocolo se comporta y se recupera deestos problemas.

## PROBLEMA 3: Creación de un sistema de autenticación segura con LDAP y SSH

### Paso 1: Configuración de LDAP y SSH
```
 import paramiko
 def create_ssh_tunnel(user, password, host, remote_host, local_port, remote_port):
 client = paramiko.SSHClient()
 client.set_missing_host_key_policy(paramiko.AutoAddPolicy())
 client.connect(host, username=user, password=password)
 # Establecer un reenvío de puertos para LDAP
 tunnel = client.get_transport().open_channel('direct-tcpip', (remote_host, remote_port),
 ('localhost', local_port))
 return client, tunnel
 def main():
 ssh_user = 'admin'
 ssh_password = 'securepassword'
 ssh_host = 'example.com'
 ldap_host = 'ldap.example.com'
 local_ldap_port = 389
 remote_ldap_port = 389
 client, tunnel = create_ssh_tunnel(ssh_user, ssh_password, ssh_host, ldap_host,
 local_ldap_port, remote_ldap_port)
 print(f"SSH tunnel established for LDAP on port {local_ldap_port}")

 # Aquí se simularían operaciones LDAP a través del túnel
 # Por ejemplo, consultas LDAP, autenticación de usuarios, etc.
 tunnel.close()
 client.close()
 if __name__ == '__main__':
 main()
```
### Resultados:
````
C:\Users\PROPIETARIO\PycharmProjects\pythonProject1\venv\Scripts\python.exe C:\Users\PROPIETARIO\PycharmProjects\pythonProject1\main.py 
Traceback (most recent call last):
  File "C:\Users\PROPIETARIO\PycharmProjects\pythonProject1\main.py", line 34, in <module>
    main()
  File "C:\Users\PROPIETARIO\PycharmProjects\pythonProject1\main.py", line 23, in main
    client, tunnel = create_ssh_tunnel(ssh_user, ssh_password, ssh_host, ldap_host, local_ldap_port, remote_ldap_port)
                     ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "C:\Users\PROPIETARIO\PycharmProjects\pythonProject1\main.py", line 7, in create_ssh_tunnel
    client.connect(host, username=user, password=password)
  File "C:\Users\PROPIETARIO\PycharmProjects\pythonProject1\venv\Lib\site-packages\paramiko\client.py", line 386, in connect
    sock.connect(addr)
TimeoutError: [WinError 10060] Se produjo un error durante el intento de conexión ya que la parte conectada no respondió adecuadamente tras un periodo de tiempo, o bien se produjo un error en la conexión establecida ya que el host conectado no ha podido responder

Process finished with exit code 1


````
### Análisis de resultados:
````


El error experimentado indica que el intento de conexión SSH ha fallado debido a un tiempo de espera. Esto podría deberse a varias razones:

El host en invocación no está accesible en la red.

Las credenciales proporcionadas son incorrectas.

Hay un problema de configuración en el servidor SSH.

Para solucionar este problema,probemos lo siguiente:

El servidor SSH está en funcionamiento y accesible desde la red en la que te encuentras.

Las credenciales de inicio de sesión (ssh_user y ssh_password) son correctas y tienen permiso para iniciar sesión en el servidor SSH.

No hay restricciones de firewall o configuraciones de red que puedan bloquear la conexión SSH.
````
### Paso 2: Implementación de seguridad
```
from OpenSSL import crypto

def create_self_signed_cert(cert_file, key_file):
    k = crypto.PKey()
    k.generate_key(crypto.TYPE_RSA, 2048)
    cert = crypto.X509()
    cert.get_subject().C = "US"
    cert.get_subject().ST = "California"
    cert.get_subject().L = "San Francisco"
    cert.get_subject().O = "My Company"
    cert.get_subject().OU = "My Organizational Unit"
    cert.get_subject().CN = "mydomain.com"
    cert.set_serial_number(1000)
    cert.gmtime_adj_notBefore(0)
    cert.gmtime_adj_notAfter(10*365*24*60*60)
    cert.set_issuer(cert.get_subject())
    cert.set_pubkey(k)
    cert.sign(k, 'sha256')
    with open(cert_file, "wt") as certfile:
        certfile.write(crypto.dump_certificate(crypto.FILETYPE_PEM, cert).decode('utf-8'))
    with open(key_file, "wt") as keyfile:
        keyfile.write(crypto.dump_privatekey(crypto.FILETYPE_PEM, k).decode('utf-8'))

create_self_signed_cert('ldap_cert.pem', 'ldap_key.pem')

```
# Resultados
````
Traceback (most recent call last):
  File "C:\Users\PROPIETARIO\PycharmProjects\pythonProject1\main.py", line 34, in <module>
    main()
  File "C:\Users\PROPIETARIO\PycharmProjects\pythonProject1\main.py", line 23, in main
    client, tunnel = create_ssh_tunnel(ssh_user, ssh_password, ssh_host, ldap_host, local_ldap_port, remote_ldap_port)
                     ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "C:\Users\PROPIETARIO\PycharmProjects\pythonProject1\main.py", line 7, in create_ssh_tunnel
    client.connect(host, username=user, password=password)
  File "C:\Users\PROPIETARIO\PycharmProjects\pythonProject1\venv\Lib\site-packages\paramiko\client.py", line 386, in connect
    sock.connect(addr)
TimeoutError: [WinError 10060] Se produjo un error durante el intento de conexión ya que la parte conectada no respondió adecuadamente tras un periodo de tiempo, o bien se produjo un error en la conexión establecida ya que el host conectado no ha podido responder

Process finished with exit code 1
````
# Análisis
````
Este código intenta establecer una conexión SSH y crear un túnel a través de ese SSH para redirigir el tráfico LDAP desde un puerto local al servidor LDAP remoto. El error TimeoutError: [WinError 10060] generalmente significa que el cliente no puede conectarse al servidor SSH dentro del tiempo de espera especificado.

Aquí hay algunas posibles causas para este error:

El servidor SSH no está disponible o no responde: Asegúrate de que el servidor SSH esté en ejecución y accesible desde la máquina donde se ejecuta este código.
Credenciales incorrectas: Verifica que el nombre de usuario y la contraseña proporcionados sean correctos y tengan permiso para conectarse al servidor SSH.
Firewall o configuración de red bloqueando la conexión: Asegúrate de que no haya restricciones en el firewall o en la configuración de red que impidan la conexión saliente desde la máquina local al servidor SSH.
Problemas de configuración de Paramiko: Asegúrate de que Paramiko esté instalado correctamente y que su uso sea compatible con el entorno en el que se está ejecutando el código.
````

### Paso 3: Evaluación de seguridad

 Discutir cómo evaluar la seguridad del sistema implementado, abordando potenciales
 vulnerabilidades como ataques de intermediario y configuraciones erróneas de certificados.
 La evaluación incluirá pruebas de penetración y revisión de configuraciones.
 

Evaluar la seguridad del sistema implementado, especialmente en un entorno que involucra conexiones SSH, túneles SSL/TLS y LDAP, es crucial para identificar y mitigar posibles vulnerabilidades. Aquí hay algunas consideraciones sobre cómo abordar estas preocupaciones:

### 1. Pruebas de Penetración:

#### a. Pruebas de Seguridad de Red:
   - Realizar escaneos de puertos para identificar servicios expuestos.
   - Utilizar herramientas como Nmap para descubrir posibles vulnerabilidades en la configuración de red.
   - Comprobar la configuración del firewall para asegurarse de que sólo los puertos necesarios estén abiertos.

#### b. Evaluación de Vulnerabilidades:
   - Utilizar herramientas de evaluación de vulnerabilidades como Nessus, OpenVAS o Nikto para identificar posibles fallos de seguridad en el sistema.
   - Realizar pruebas de inyección de código SQL y XSS en aplicaciones web, si las hay.

#### c. Pruebas de Seguridad de Aplicaciones:
   - Revisar el código fuente de las aplicaciones para identificar posibles vulnerabilidades de seguridad.
   - Utilizar herramientas como OWASP ZAP para realizar pruebas de seguridad de aplicaciones web.

### 2. Revisión de Configuraciones:

#### a. Configuraciones de SSH:
   - Revisar la configuración del servidor SSH para asegurarse de que sólo se permitan métodos de autenticación seguros.
   - Configurar adecuadamente las claves SSH y deshabilitar el acceso con contraseña si es posible.
   - Implementar reglas de firewall para limitar el acceso al servidor SSH desde direcciones IP específicas si es necesario.

#### b. Configuraciones de Certificados SSL/TLS:
   - Verificar que los certificados SSL/TLS utilizados sean válidos y estén correctamente configurados.
   - Utilizar herramientas como SSL Labs para evaluar la configuración SSL/TLS y detectar posibles vulnerabilidades, como configuraciones débiles de cifrado o caducidad de certificados.

#### c. Configuraciones de Servidores LDAP:
   - Revisar la configuración del servidor LDAP para asegurarse de que sólo se permitan conexiones cifradas.
   - Configurar adecuadamente los permisos de acceso para restringir el acceso sólo a usuarios autorizados.
   - Implementar políticas de seguridad de contraseñas para evitar contraseñas débiles.

### 3. Mitigación de Vulnerabilidades:

#### a. Aplicar Parches y Actualizaciones:
   - Mantener actualizados todos los sistemas y software para mitigar vulnerabilidades conocidas.

#### b. Monitoreo de Seguridad:
   - Implementar sistemas de monitoreo de seguridad para detectar y responder rápidamente a posibles ataques.
   - Utilizar soluciones de detección de intrusiones (IDS) y prevención de intrusiones (IPS) para detectar y bloquear intentos de ataques.

#### c. Capacitación del Personal:
   - Proporcionar capacitación en seguridad informática al personal para aumentar la conciencia sobre las amenazas de seguridad y promover prácticas seguras.

### 4. Auditorías de Seguridad:
   - Realizar auditorías de seguridad periódicas para evaluar continuamente la postura de seguridad del sistema e identificar posibles áreas de mejora.

Al seguir estas medidas y realizar pruebas de penetración y revisiones de configuraciones de forma regular, se puede fortalecer la seguridad del sistema y mitigar posibles vulnerabilidades, incluyendo ataques de intermediario y configuraciones erróneas de certificados.


## PROBLEMA 4: Simulación de interpolaridad de red con múltiples protocolos

### Contexto: 

Simular un entorno de red que utilice múltiples protocolos de la pila TCP/IP, asegurando la interoperabilidad entre dispositivos que utilizan diferentes configuraciones dered.

- *Para tu presentación y código a presentar puedes utilizar:*

#### Objetivos:
1. Simulación de protocolos de Red: Crear un entorno simulado que incluya IP, ICMP,IGMP, y ARP para observar y gestionar la comunicación entre dispositivos.
2. Implementación de la simulación en Python: Utilizar Python para crear scripts quesimulen el envío y recepción de paquetes utilizando estos protocolos.
3. Evaluación de interoperabilidad: Analizar cómo estos protocolos interactúan ygestionan la conectividad, especialmente en escenarios de alta densidad de red ytráfico multicast.
4. Uso de R-utilities para monitoreo y resolución de problemas: Implementar y discutircómo herramientas como traceroute, ping y otras utilidades pueden ayudar adiagnosticar y resolver problemas en la red.

### Paso 1: 
- Simulación de protocolos de red en PythonUsaremos Python para simular la generación y el manejo de paquetes de red para IP, ICMP,IGMP y ARP. Utilizaremos la biblioteca scapy, que es muy potente para manipular y enviarpaquetes de red.

##### Código Python para la simulación de protocolos:
```
rom scapy.all import *

def simulate_ip():
    packet = IP(dst="192.168.1.1") / ICMP() / "Hello, this is an IP packet"
    send(packet)

def simulate_icmp():
    icmp_echo = IP(dst="192.168.1.1") / ICMP(type=8, code=0) / "Ping"
    send(icmp_echo)

def simulate_igmp():
    igmp_packet = IP(dst="224.0.0.1", proto=2) / Raw(load="\x16\x00\x00\x00" + "224.0.0.1")
    send(igmp_packet)

def simulate_arp():
    arp_request = ARP(pdst='192.168.1.2')
    send(arp_request)

def main():
    simulate_ip()
    simulate_icmp()
    simulate_igmp()
    simulate_arp()

if __name__ == "__main__":
    main()
```
#### Resultados:
```
Sent 1 packets.

Sent 1 packets.

Sent 1 packets.

Sent 1 packets.
```
El código proporcionado simula el envío de paquetes para los protocolos IP, ICMP, IGMP y ARP utilizando la biblioteca Scapy en Python, donde en cada función de simulación, se construye un paquete utilizando los campos específicos del protocolo correspondiente y se envía utilizando la función `send()` de Scapy. El objetivo de este script es poder demostrar cómo se pueden enviar diferentes tipos de paquetes de red utilizando Scapy para realizar pruebas o simulaciones den treo de una red, sin embargo, vale la pena mencionar que la simulación de IGMP en este código no utiliza la clase IGMP de Scapy, sino que construye manualmente este paquete de IGMP utilizando la capa Raw, lo que puede no ser tan preciso o completo como el uso de la clase IGMP proporcionada por Scapy, pero que no se lograba ejecutar.

### Paso 2: Evaluación de interoperabilidad
- **Después de simular cada protocolo, observaremos cómo los paquetes son gestionados y dirigidos a través de la red. Esto ayudará a identificar problemas de interoperabilidad y eficiencia en la comunicación entre dispositivos.**

Despúes de haber realizado la simulación es muy útil para lograr identificar problemas de interoperabilidad y eficiencia en la comunicación entre dispositivos donde es importante asegurarse de que la red y los dispositivos involucrados estén configurados correctamente para responder a estos protocolos y manejar los paquetes como se espera y de manera eficiente.

### Paso 3: Uso de R-utilities para diagnóstico

- Implementaremos scripts para utilizar R-utilities como traceroute y ping, y simular cómo sepueden usar para monitorear y diagnosticar problemas en la red.


#### Código Python para Utilizar R-utilities:

```
import os

def run_traceroute(target):
    print(f"Traceroute a {target}:")
    response = os.system(f"traceroute {target}")
    print(response)

def run_ping(target):
    print(f"Ping a {target}:")
    response = os.system(f"ping -c 4 {target}")
    print(response)

if __name__ == "__main__":
    target_ip = '192.168.1.1'
    run_traceroute(target_ip)
    run_ping(target_ip)

```
#### Resultados:
```
Traceroute a 192.168.1.1:
32512
Ping a 192.168.1.1:
32512
```

Este código implementa dos funciones, `run_traceroute` y `run_ping`, que utilizan la biblioteca estándar `os` para ejecutar los comandos de traceroute y ping en el sistema operativo. Cada función toma un parámetro `target`, que es la dirección IP del destino al que se realizará el traceroute o el ping, donde dentro de cada función, se imprime un mensaje indicando la acción que se está realizando (traceroute o ping) y la dirección IP del destino, luego, se ejecuta el comando correspondiente utilizando `os.system()`, y la salida del comando se imprime en la consola, en el bloque `if __name__ == "__main__":`, se define una dirección IP de destino en `target_ip` y se invocan las funciones `run_traceroute` y `run_ping` con esta dirección IP, basicamente este código proporciona una forma simple de ejecutar comandos de red desde Python y visualizar los resultados en la consola.


