# ACTIVIDAD 11: 
PREGUNTAS Y RESPUESTAS

# EXPOSICIÓN:
https://github.com/Fx2048/COMU_TEAM/blob/main/TAREAS/Actividad_11_Exposicion.md

# Problema 4: Análisis y diseño de red Peer-to-Peer (P2P)

Escenario: Una startup tecnológica desea implementar una red P2P robusta para permitir elintercambio eficiente de recursos computacionales entre usuarios distribuidosgeográficamente. Esta red debe ser capaz de manejar intercambios dinámicos de archivos,distribución de carga, y debe incorporar medidas de seguridad para prevenir accesos noautorizados

Preguntas:

1. Describe cómo se diferenciaría esta red P2P de una red cliente-servidor en términosde diseño de red y topología.

2. ¿Qué protocolos específicos usarías para gestionar las comunicaciones y elintercambio de archivos en esta red?

3. Analiza los posibles problemas de seguridad asociados con una red P2P y proponesoluciones para mitigar estos riesgos.
4. Evalúa el impacto de incorporar nodos que actúan tanto como clientes comoservidores. ¿Cómo gestionarías el balanceo de carga?

Parte 1: Implementación de la Red P2P con Python

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
 # ejemplos de uso
 node = Peer('127.0.0.1', 5000)
 node.connect_to_peer('127.0.0.1', 6000)
````
#  Parte 2: Gestión de recursos y distribución de carga

Parte 3: Seguridad en la Red P2P
````
 import hashlib
 import os
 def generate_key(password):
 salt = os.urandom(16)
 key = hashlib.pbkdf2_hmac('sha256', password.encode('utf-8'), salt, 100000)
 return salt + key
 def verify_key(stored_key, provided_password):
 salt = stored_key[:16]
 key = stored_key[16:]
 new_key =hashlib.pbkdf2_hmac('sha256', provided_password.encode('utf-8'), salt,
 100000)
 return new_key == key
 password = "secure_password"
 key = generate_key(password)
 print("Key generated successfully.")
 print("Verification:", verify_key(key, password)
 import time
 def monitor_peers(peers):
 while True:
 for peer in peers:
 try:
 peer.send(b'ping')
 response = peer.recv(1024)
 if response != b'pong':
 raise Exception("Peer is not responding correctly.")
 except Exception as e:
 print(f"Peer {peer.getpeername()} failed: {e}")
 peers.remove(peer)
 time.sleep(60) # Check every minute
 # In the Peer class, handle 'ping' messages
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
````
