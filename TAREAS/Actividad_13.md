# Actividad 13 :  TCP/IP


# Problema 3: Creación de un sistema de autenticación segura con LDAP y SSH

## Paso 1: Configuración de LDAP y SSH
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
# Resultados:
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
# Análisis de resultados:
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
 Paso 2: Implementación de seguridad
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
 open(cert_file, "wt").write(crypto.dump_certificate(crypto.FILETYPE_PEM,
cert).decode('utf-8'))
 open(key_file, "wt").write(crypto.dump_privatekey(crypto.FILETYPE_PEM,
k).decode('utf-8'))
create_self_signed_cert('ldap_cert.pem', 'ldap_key.pem')

```

# Paso 3: Evaluación de seguridad

 Discutir cómo evaluar la seguridad del sistema implementado, abordando potenciales
 vulnerabilidades como ataques de intermediario y configuraciones erróneas de certificados.
 La evaluación incluirá pruebas de penetración y revisión de configuraciones.
