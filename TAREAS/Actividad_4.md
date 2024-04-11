# Actividad 4: Configuración inicial de un Switch
##### ENLACE A LA ACTIVIDAD 4 EN SOFTWARE https://github.com/Fx2048/COMU_TEAM/tree/main/CISCO_PACKET_TRACER

![image](https://github.com/Fx2048/COMU_TEAM/assets/131219987/ffb6f924-4197-4f30-87bc-319013a86b68)


Preguntas
Responde las siguientes preguntas:
- a) **¿Cuántas interfaces Fast Ethernet tiene el switch?**
  
- ![image](https://github.com/Fx2048/COMU_TEAM/assets/131219987/281411b0-8a02-44af-a7a4-53a8247cdb3f)


  **Rpta//**.En total tenemos 24 Inteface Fast Ethernet( son puertos en un switch que admiten velocidades de hasta 100 Mbps),los 24 puertos nos permite admitir conexiones de hasta 100 Mbps(megabit por segundo) cada uno. Estos puertos son esenciales para las capacidades de transferencia de datos en una red local.
   
- **b) ¿Cuántas interfaces Gigabit Ethernet tiene el switch?**

![image](https://github.com/Fx2048/COMU_TEAM/assets/131219987/ade5ff52-f174-45be-82b1-3369d9e18efe)


  **Rpta//.** Presenta dos gigabits ethernet(son puertos en un switch que admiten velocidades de hasta 1 Gbps o más).
  
- **c) ¿Cuál es el rango de valores que se muestra para las líneas vty?**

![image](https://github.com/Fx2048/COMU_TEAM/assets/131219987/470d2ba8-7255-4ca6-a867-33b5a4b3eeae)


  **Rpta//**.El rango de lineas vty son de 0, 4 a 5 al 15.(son las líneas de terminal virtual del enrutador, utilizadas exclusivamente para controlar las conexiones Telnet entrantes. )Estas líneas permiten administrar el dispositivo de forma remota.
  
- **d) ¿Qué comando muestra el contenido actual de la memoria de acceso aleatorio no volátil
(NVRAM)?**

![image](https://github.com/Fx2048/COMU_TEAM/assets/131219987/f5ae0cdc-5b78-4972-9cad-5a1b11f8c38e)


  **Rpta//**.El comando seria: show startup-config. Proporciona la configuración almacenada en la NVRAM, que incluye la configuración inicial del dispositivo.
  
- **e) ¿Por qué el switch responde con "startup-config no está presente"?**

  **Rpta//.** Aparece así porque no hemos guardado nada en la memoria, todo sigue estando en la memoria ram, y esto es prueba cuando queremos guardar algo, está todavía en la Memoria RAM.

Proporciona acceso seguro a la línea de consola.

Para proporcionar un acceso seguro a la línea de la consola, acceda al modo config-line y establezca la contraseña de consola en cesar.
S1# configure terminal

Enter configuration commands, one per line. End with CNTL/Z.

S1(config)# line console 0

S1(config-line)# password cesar

S1(config-line)# login

S1(config-line)# exit

S1(config)# exit

%SYS-5-CONFIG_I: Configured from console by console

S1#

## Pregunta:

- **¿Por qué se requiere el comando login?**

  **Rpta//**. El comando login se utiliza para requerir autenticación al acceder a la línea de consola. Esto significa que cuando alguien intenta acceder a través de la línea de consola, se le pedirá que ingrese una contraseña (en este caso, "cesar") para verificar su identidad. En otras palabras, sirve para poner una contraseña en la consola y sea posible, sin ello no va a funcionar


Verifica si la contraseña de enable secret se agregó al archivo de configuración.
Introduce el comando show running-config nuevamente para verificar si la nueva contraseña de
enable secret está configurada.

Nota: Puedes abreviar show running-config como

S1# show run

## Preguntas:
- **¿Qué se muestra como contraseña de enable secret?**

![image](https://github.com/Fx2048/COMU_TEAM/assets/131219987/785ddbc0-e7c5-46f8-8ad5-656edba2f00e)


  **Rpta//**. La contraseña de enable secret se muestra como una cadena encriptada, lo que la hace no legible en el archivo de configuración.Mostrándonos una contraseña encriptada
  
- **¿Por qué la contraseña de enable secret se ve diferente de lo que se configuró?**

  **Rpta//.** La contraseña de enable secret se ve diferente porque, por defecto, el IOS de Cisco encripta las contraseñas de forma automática para mejorar la seguridad. Además a diferencia de una contraseña plana, ahora nos muestra una contraseña encriptada.
 
Encripta las contraseñas de consola y de enable.

Como notó en el paso anterior, la contraseña enable secret estaba encriptada, pero las contraseñas
enable y console todavía estaban en texto plano. Ahora encriptamos estas contraseñas de texto no
cifrado con el comando service password-encryption.

S1# config t

S1(config)# service password-encryption

S1(config)# exit

## Pregunta:
- **Si configuras más contraseñas en el switch, ¿se mostrarán como texto no cifrado o en forma cifrada
en el archivo de configuración? Explica.**

  **Rpta//.** Cuando se utiliza el comando service password-encryption, todas las contraseñas configuradas después de este comando, incluidas las de consola y enable, se mostrarán en forma cifrada en el archivo de configuración.


Configura un aviso de mensaje del día (MOTD).

El conjunto de comandos de Cisco IOS incluye una característica que permite configurar los
mensajes que cualquier persona puede ver cuando inicia sesión en el switch. Estos mensajes se
denominan “mensajes del día” o “avisos de MOTD”. Coloca el texto del mensaje en citas o utilizando
un delimitador diferente a cualquier carácter que aparece en la cadena de MOTD.

S1# config t

S1(config)# banner motd "This is a secure system. Authorized Access Only!

S1(config)# exit

%SYS-5-CONFIG_I: Configured from console by console

S1#

## Preguntas:
-**Cuándo se muestra este aviso?**

  **Rpta//**. Nos muestra después de que un usuario inicia sesión en el switch. Es la primera información que ven al acceder a la interfaz de línea de comandos (CLI).
- **¿Por qué todos los switches deben tener un aviso de MOTD?**

   **Rpta//**. Todos los switch deben tener un banner MOTD para evitar que personas no autorizadas entren, es más que todo para resguardar la seguridad.
## 4 . Guarda y verifica archivos de configuración en NVRAM

Verifica que la configuración sea precisa mediante el comando show run.
Guarda el archivo de configuración. Tu has completado la configuración básica del switch. Ahora
haga una copia de seguridad del archivo de configuración en ejecución a NVRAM para garantizar
que los cambios que se han realizado no se pierdan si el sistema se reinicia o se apaga.

S1# copy running-config startup-config

Destination filename [startup-config]?[Enter]

Building configuration...

[OK]

Cierre la ventana de configuración para S1

## Preguntas:
- ¿Cuál es la versión abreviada más corta del comando copy running-config startup-config?

  Rptt//. La versión abreviada más corta del comando es copy run start. La forma abreviada es debe ser única, y copy se abrevia con “cop r s” o “cop r st”.
- Examine el archivo de configuración de inicio.¿Qué comando muestra el contenido de la NVRAM?

  Rptt//. El comando que muestra el contenido de la NVRAM es show startup-config.

Escriba sus respuestas aquí.
- ¿Todos los cambios realizados están grabados en el archivo?

  Rptt//. Sí, basicamente es lo mismo de running config, pero no se va a borrar. Todos los cambios realizados están grabados en el archivo de configuración de inicio (startup-config) en la NVRAM. Esto asegura que los cambios persistan incluso si el sistema se reinicia o se apaga.
 
