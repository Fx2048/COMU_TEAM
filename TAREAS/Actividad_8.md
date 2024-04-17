# Actividad 8: Comunicaciones de TCP y UDP

### Objetivos 
- Parte 1: Generar tráfico de red en el modo de simulación
- Parte 2: Examinar la funcionalidad de los protocolos TCP y UDP
  
### Examina la multiplexación a medida que el tráfico cruza la red

- **¿Cómo se llama esto?**

Se llama multiplexación, es transmitir diferentes datos por un mismo medio pero no simultaneamente.

![image](https://github.com/Fx2048/COMU_TEAM/assets/151795724/5b3a0cb3-d1e4-4852-a2fc-e6be0953ef13)

- **Aparece una variedad de PDU en la lista de eventos en el Panel de simulación. ¿Cuál es el significado de los diferentes colores?**
  
Significa los protocolos que se usa en cada PDU.

### Examinar la funionalidad de los prtocolos TCP y UDP

- **¿Por qué tardó tanto en aparecer la PDU HTTP?**

Es debido que primero debe establecerse una conexión tcp entre cliente y servidor para que el tráfico pueda comenzar.

- **¿Cómo se rotula la sección?**

 Mediante un TCP. 

- **¿Se consideran confiables estas comunicaciones?** 

Sí, el TCP es un protocolo confiable a diferenca del UDP que no lo es.

- **¿Qué indicadores TCP se establecen en esta PDU?**

![image](https://github.com/Fx2048/COMU_TEAM/assets/151795724/dbcb9d49-398d-414b-99a0-556e6f24d226)

Se establecen ACK y PSH donde tiene el (1).

![image](https://github.com/Fx2048/COMU_TEAM/assets/151795724/ac596107-3758-4eaa-8b08-342a254a7ee2)

- **¿En qué cambiaron los números de puerto y de secuencia?**

Tanto el puerto de origen como el puerto de destino han cambiado de posición. Y el seq number sigue igual, y el flag están en la misma posición. Pero el ack ha cambiado(numero de reconocimiento).

![image](https://github.com/Fx2048/COMU_TEAM/assets/151795724/3a781556-ead0-4f74-868b-637e486b0511)

- **¿Qué información aparece ahora en la sección TCP? ¿En qué se diferencian los números de puerto y de secuencia con respecto a las dos PDU anteriores?**

Ahora se ha invertido el puerto de origen y de destino, y el ack ha aumentado a 234, el de seq number a 103, y el flag tiene los indicadores en ack y fin. 

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/7513f8de-92c3-43e6-8972-61058f1d326c)

- **¿Se consideran confiables estas comunicaciones?**

Sí, se considera que son confiables.

- **¿Cuál es el valor en el campo de bandera?**

El valor es de indicador  SYN.

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/8b41625d-9ad9-445d-b30d-d78955482d5c)
![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/b7848f03-f9b8-4474-9bcf-836f91152979)

- **¿En qué cambiaron los números de puerto y de secuencia?**

Se diferencian en que se ha invertido el puerto de destino y de origen, y ,también permanece el seq number y ,ha cambiado el ack number  y el flag de SYN, adicionó a ACK. 

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/88623eb2-584e-446e-b4bd-6fe13228a838)

- **¿En qué se diferencian los números de puerto y secuencia de los resultados anteriores?**

Se diferencian a los números anteriores dado que ha cambiado el número de puerto de origen, el puerto de destino,(invertidos) y el ack se mantuvo, y el seq number se cambió , y el flag se cambió su indicador a ACK. 

- **¿Cuál es el mensaje del servidor?**

El mensaje del servidor es WELCOME TO PT FTP SERVER.

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/396adb79-a0df-4f6d-be83-163a6465b6fb)

- **¿Qué es el protocolo de capa 4?**

El protocolo de capa 4 es UDP.

- **¿Se consideran confiables estas comunicaciones?**

No son confiables.

- **¿Por qué no hay números de secuencia y reconocimiento?**

Porque udp no necesita ser una conexi´n confiable, por eso no tiene todos los valores que tcp tiene.

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/87f1e59f-80b6-4fca-a689-89a77ee353a7)

- **¿En qué cambiaron los números de puerto y de secuencia?**

Se han invertido.

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/455ee563-8d01-44fb-9eac-7843e3ff59c9)

- **¿Cómo se llama la última sección de la PDU?**

La última sección se llama DNS.

- **¿Cuál es la dirección IP para el nombre multiserver.pt.ptu?**

El IP para el multiserver.pt.ptu es: 192 .168. 1.254.

- **¿Qué protocolo de la capa de transporte utiliza el tráfico de correo electrónico?**

El protocolo que utiliza el tráfico de correo electrónico es el TCP.

- **¿Se consideran confiables estas comunicaciones?**

Si se consideran confiables.

- **¿En qué cambiaron los números de puerto y de secuencia?**

Tiene un ACK y un  SYN a diferencia del anterior, se invirtieron los puertos y el ack nnumber cambió, mientras que el seq number permanece.

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/5d9992d6-a59f-491c-afd0-47f927732a70)

- **¿En qué se diferencian los números de puerto y de secuencia con respecto a los dos resultados anteriores? ¿En qué se diferencian los números de puerto y de secuencia con respecto a las dos PDU anteriores?**

Se ha invertido con respecto al anterior, los puertos, y el ack number se ha mantenido, y el seq number subió a 1, mientras que el flag cambió a ACK su indicador, y ya no tiene SYN, done ha mantenido el puerto de origen, pero cambió el flag quitandole el ACK.

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/aaa8e942-f7be-4ece-803f-917b2ab5fe76)

- **¿Qué protocolo de correo electrónico se relaciona con el puerto TCP 25?**

El protocolo que se relaciona con el puerto 25  es el SMTP.

- **¿Qué protocolo se relaciona con el puerto TCP 110?**

EL protocolo que se relaciona con el puerto TPC 110 es el POP 3.
