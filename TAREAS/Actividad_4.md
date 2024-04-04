# Actividad 4: Configuración inicial de un Switch
Preguntas
Responde las siguientes preguntas:
a) ¿Cuántas interfaces Fast Ethernet tiene el switch?
b) ¿Cuántas interfaces Gigabit Ethernet tiene el switch?
c) ¿Cuál es el rango de valores que se muestra para las líneas vty?
d) ¿Qué comando muestra el contenido actual de la memoria de acceso aleatorio no volátil
(NVRAM)? show star
e) ¿Por qué el switch responde con "startup-config no está presente"?

Proporciona acceso seguro a la línea de consola.
Para proporcionar un acceso seguro a la línea de la consola, acceda al modo config-line y establezca
la contraseña de consola en cesar.
S1# configure terminal
Enter configuration commands, one per line. End with CNTL/Z.
S1(config)# line console 0
S1(config-line)# password cesar
S1(config-line)# login
S1(config-line)# exit
S1(config)# exit
%SYS-5-CONFIG_I: Configured from console by console
S1#
Pregunta:
¿Por qué se requiere el comando login?


Verifica si la contraseña de enable secret se agregó al archivo de configuración.
Introduce el comando show running-config nuevamente para verificar si la nueva contraseña de
enable secret está configurada.
Nota: Puedes abreviar show running-config como
S1# show run
Preguntas:
¿Qué se muestra como contraseña de enable secret?

¿Por qué la contraseña de enable secret se ve diferente de lo que se configuró?

Encripta las contraseñas de consola y de enable.
Como notó en el paso anterior, la contraseña enable secret estaba encriptada, pero las contraseñas
enable y console todavía estaban en texto plano. Ahora encriptamos estas contraseñas de texto no
cifrado con el comando service password-encryption.
S1# config t
S1(config)# service password-encryption
S1(config)# exit
Pregunta:
Si configuras más contraseñas en el switch, ¿se mostrarán como texto no cifrado o en forma cifrada
en el archivo de configuración? Explica.


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
Preguntas:
¿Cuándo se muestra este aviso?
¿Por qué todos los switches deben tener un aviso de MOTD?



4 . Guarda y verifica archivos de configuración en NVRAM
Verifica que la configuración sea precisa mediante el comando show run.
Guarda el archivo de configuración. Tu has completado la configuración básica del switch. Ahora
haga una copia de seguridad del archivo de configuración en ejecución a NVRAM para garantizar
que los cambios que se han realizado no se pierdan si el sistema se reinicia o se apaga.
S1# copy running-config startup-config
Destination filename [startup-config]?[Enter]
Building configuration...
[OK]
Cierre la ventana de configuración para S1
Preguntas:
¿Cuál es la versión abreviada más corta del comando copy running-config
startup-config?Examine el archivo de configuración de inicio.¿Qué comando muestra el contenido
de la NVRAM?
Escriba sus respuestas aquí.
¿Todos los cambios realizados están grabados en el archivo?
