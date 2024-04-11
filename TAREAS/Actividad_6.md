♾️ Actividad 4: Crear una red con un switch y un router - Modo Físico

## 📂ENLACE A LA ACTIVIDAD 6 EN SOFTWARE 

https://github.com/Fx2048/COMU_TEAM/tree/main/CISCO_PACKET_TRACER


## 📂Preguntas Responde las siguientes preguntas:

### 🔼 a)  ¿Por qué los pings no fueron correctos?  
#### ✅En el caso presentado , estos no han sIdo correctos porque  no se ha configurado la direccion IP  o no 
están conectados.

### 🔼 En unaventana con el símbolo del sistema en la PC-A, haga ping a la PC-B.
 Nota: Si los pings no son correctos, es posible que debas desactivar el Firewall.
 
 ## 📂Pregunta
¿Fueron correctos los pings? Explica. 

#### ✅No fueron correctos los pings, porque el router lleva el tráfico en sus dos 
raíces, Giga Ethernet 0/0 , y gigaethernet 0/1, y esto es puesto a  la configuracion la cual no ha sido configurada por completo.

### 🔼¿Qué código se utiliza en la tabla de enrutamiento para indicar una red conectada 
directamente?

#### ✅Se usa el código (L)local,(C)connected, (S)static, (R)rip ,(M) mobile y (B)BGP respectivamente.

### 🔼¿Cuántas entradas de ruta están codificadas con un código C en la tabla de enrutamiento? 

#### ✅ Las entradas expuestas son las de tipo C mostradas a continuación:
-  192.168.0.0/24 is directly connected. GigabitEthernet 0/0/0/
-  192.168.0.0/32 is directly connected , GigabitEthernet 0/0/1.

### 🔼Qué tipos de interfaces están asociadas a las rutas con código C? 

#### ✅Las interfaces asociadas son las siguientes:
-Gigaethernet 0/0/0
-Gigaethernet 0/0/1 

### 🔼¿Cuál es el estado operativo de la interfaz G0/0/1? 
 
 #### ✅Conectado de momento (Is up connected)
 
### 🔼¿Cuál es la dirección de control de acceso a los medios (MAC) de la interfaz G0/0/1? 

#### ✅Es la siguiente: 0060_6C92 (BIS 0060::6C83 6002)

### 🔼¿Cómo se muestra la dirección de Internet en este comando?

#### ✅ De la siguiente manera: 192.160.1.1/2

## 📂Preguntas 

### 🔼1. Si la interfaz G0/0/1 se mostrará administratively down, ¿qué comando de configuración de 
interfaz usaría para activar la interfaz? 

#### ✅ La configuración de las interfaces se realiza desde:
1.Submodo de configuración de interfaces.
2.Digitamos interface cuando nos encontramos en modo de configuracion global (lo cual cambiaría a  config if)
3.Posteriormente, cambiamos al  comando "no shut" o "not shutdown" , porque este se habilita para cambiar interfaces.
4.Ejecutamos.
5.La interface debe activarse.


### 🔼2. ¿Qué ocurriría si hubiera configurado incorrectamente la interfaz G0/0/1 en el router con una 
dirección IP 192.168.1.2?

#### ✅La PC-A no podría hacer pin a PCB.Puntualmente, esto es debido a que la PCB está en una red diferente a la de PCA 
que requiere del router del waterwall determinado para dirigir estos paquetes , la PC-A por su parte está 
configurada para dirigir estos paquetes y utilizar solamente la dirección "IP 162 .168 .1.1" , para el 
ruoter del waterwall predeterminado, pero; esta dirección no está asignada a ningún dsipositivo en la 
LAN, asi que cualquier paquete que vaya  a ser enviado para su enrutamiento nunca llegará al 
destino. 
