## ACTIVIDAD 7: INVESTIGACIÓN DE LOS MODELOS TCP/IP Y OSI

### OBJETIVOS:
- Parte 1: Examinar el tráfico web HTTP
-  Parte 2: Mostrar elementos de la suite de protocolos TCP/IP
-  Utiliza el archivo .pka que acompaña la actividad.

## EXAMINAR EL TRÁFICO WEB HTTP
### Responde las diguientes preguntas:

### Genera tráfico web (HTTP)

- **Observa la página del navegador web del cliente web. ¿Cambió algo?**
   
  Lo que se puede observar es que se accedió exitosamente a la página.
  ![image](https://github.com/Fx2048/COMU_TEAM/assets/151795724/7df9d172-2cb6-49d9-8a69-2b7f581998b6)
  
### Explora el contenido del paquete HTTP
![image](https://github.com/Fx2048/COMU_TEAM/assets/151795724/4a8b2548-c2ef-4644-84f1-761b9f07afa1)

- **¿Qué información se indica en los pasos numerados directamente debajo de los cuadros *capas de entrada* y *capas de salida***

Nos muestra información de como el cliente envía una solicitud HTTP al servidor.

![image](https://github.com/Fx2048/COMU_TEAM/assets/151795724/51a570a3-a91a-4100-a4b6-c78a1471b529)
- **¿Cuál es el valor del *puerto Dst* para la capa 4 en la columna *Capas de salida?***

El DST es el puerto de destino, donde nos indica que para la capa 4 es el puerto 80.

- **¿Cuál es el destino?, ¿Vaor IP para la capa 3 en la columna Capas de salida?**

El puerto de destino para le capa 3 es 192.16.1.254.

- **¿Qué información se muestras en la Capa 2 en la columna *Capas de salida?***

Nos muestra el MAC de origen y el MAC de destino, es decir nos da información de ambas MAC.

- **¿Cuál es la información frecuente que se indica en la sección IP de detalles de PDU comparada con la información que se indica en la ficha Modelo OSI? ¿Con qué capa se relaciona?**

En la capa de IP, la información que tiene en común es la direccipon tanto como de origen y de destino, relacionados a la capa 3.

![image](https://github.com/Fx2048/COMU_TEAM/assets/151795724/53b0cb39-d882-417c-91c6-7bfc6354bc73)

- **¿Cuál es la información frecuente que se indica en la sección IP de Detalles de PDU comparada con la información que se indica en la ficha Modelo OSI?**

En TSP, la infromación que se tiene en común es entre el puerto de origen y de destino, relacionados a la capa 4.

- **¿Cuál es el host que se indica en la sección HTTP de Detalles de PDU? ¿Con qué capa se relacionaría esta información en la ficha Modelo OSI?**

El host es www.osi.local, que se situa en la capa 7.

- **Compara la información que se muestra en la columna Capas de entrada con la de la columna Capas de salida: ¿cuáles son las diferencias principales?**

Si nos fijamos en la capa 1 y 7 son exactamente iguales, lo que cambia es en la capa 2 hasta la 4 tanto en ambas columnas, ya que cambia el posicionamiento de la MAC de origen y destino, donde igualemente en la capa 3 cambia dirreción IP de origen y destino viciversa, y finalmente en la capa 4 cambia los puertos de origen y destino.

![image](https://github.com/Fx2048/COMU_TEAM/assets/151795724/08fe0254-5ca4-4701-941c-417dddb3673e)

- **Haz clic en el último cuadro coloreado de la columna Información.Explica los resultados.**

Nos aparece dos pestañas: Osi mode, y inbound pdu details, porque son la información que están llegando del servidor al cliente web. 

![image](https://github.com/Fx2048/COMU_TEAM/assets/151795724/75747f92-1104-4603-b794-18c7b8660777)

## MOSTRAR ELEMENTOS DE LA SUITE DE PROTOCOLOS TPC/IP

### Ver eventos adicionales

- **¿Qué tipos de eventos adicionales se muestran?**

Tenemos DNS, ARP, TCP Y HTTP, donde se han agregado 3 protocolos más aparte de HTTP.

![image](https://github.com/Fx2048/COMU_TEAM/assets/151795724/900e1427-e07b-4e78-9cb4-36e4fa3b7dea)

- **¿Qué información se indica en NOMBRE: en la sección CONSULTA DNS?**

En la sección de DNS QUERY  nos indica www.osi.local 

- **¿En qué dispositivo se capturó la PDU?**

Se capturo en At Device, es decir en Web client.

![image](https://github.com/Fx2048/COMU_TEAM/assets/151795724/5770109c-38ff-4326-abe4-4d32ca8aed3d)

- **¿Cuál es el valor que se indica junto a DIRECCIÓN: en la sección RESPUESTA DE DNS de Detalles de la PDU entrante?**

La dirección que aparece es 192.168.1.254 donde este valor es la dirreción del servidor web, porque de ahi esta llegando el evento que se esta tratando.

![image](https://github.com/Fx2048/COMU_TEAM/assets/151795724/da2a9007-db3f-4922-af99-6c708e046daf)

-  **¿Cuál es la información que se muestra en los elementos 4 y 5?**

En el elemento 4 nos indica que la conección TCP se ha realizado de manera exitosa, mientras que en la 5 nos indica que el dispositivo a estabelcido la conección en estado ESTABLISHED (estado establecido).

![image](https://github.com/Fx2048/COMU_TEAM/assets/151795724/412f2748-9280-4a92-8f30-64f16a7e41b0)

-  **¿Cuál es el propósito de este evento, según la información proporcionada en el último elemento de la lista (debe ser el elemento 4)?**

Nos indica que el dispositivo ha sido estblecido en estado cerrado, es decir ha finalizado la conección TCP.

#### PREGUNTAS:

- **Sobre la base de la información que se analizó durante la captura de Packet Tracer, ¿qué número de puerto escucha el servidor web para detectar la solicitud web?**

El servidor web esta escuchando en el puerto 80.

![image](https://github.com/Fx2048/COMU_TEAM/assets/151795724/a37c002e-0945-48c7-bcce-f8bcf423636d)

- **¿Qué puerto escucha el servidor web para detectar una solicitud de DNS?**

El solicitud DNS está escuchando al servidor web en el puerto 53.
