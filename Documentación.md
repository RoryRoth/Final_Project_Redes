# Final_Project_Redes 

### Héctor Diaz, Juan Manuel Deutsch, Santiago Contreras



El presente documento presentará el desarrollo del projecto final de la asignatura de Redes, cuyo objetivo final es la aplicación de los contenidos y conceptos adquiridos durante el semestre relacionados al manejo, configuración y sustentación de varias redes LAN conectadas entre si mediante una red WAN. Además de demostrar un manejo consecuente con las actividades desarrolladas previamente en la herramienta de simulación de redes Cisco Packet Tracer. 

#### PROCEDIMIENTO:

1/ Configuración de las redes LAN y VLAN en las cuatro ubicaciones (Campus, Oficinas, Casa IoT, Servidores). Para este paso, todas las redes fueron cableados de cierta forma para que el resultado final sea una topología de red en Árbol.

  ***CAMPUS:***
   La conexión de la red de Campus consiste en tres redes LAN conectradas entre si mediante el switch individual de cada una y uno más conectado a todos los anteriores para logar la conexión correcta de la VLAN. Este último switch esta conectado a un wireless router que a su vez está conectado a el router proncipal que conecta a las demás redes LAN. Además este ubicación cuenta con un servidor DHCP configurado con una dirección IPv4 de entrada manual por el administrador de la red.
  
  ![image](https://user-images.githubusercontent.com/89588991/198382024-5855f2d1-4639-4e83-b9fc-ad7202c5c5ec.png)
  
  ***OFICINAS:***
   La red LAN de las oficinas consiste en varias laptops conectadas inálambricamente a un wireless router; para conectar dichas laptops es necesario cambiar su placa de red de una alámbrica a una inálambrica. Además, el router también tiene conectados de forma inálambrica una tablet y un smartphone. Este router se vincula directamente con un multilayer switch el cual nos permite crear la tabla de enrutamiento y dinamizar la velocidad de la red. A este multilayer switch encontramos conectado un PC que es usado para monitorear y administrar la red, un controlador inálambrico de la red LAN y un servidor DHCP.
  
  ![image](https://user-images.githubusercontent.com/89588991/198383518-6e8b13bb-2185-4b65-bb64-db22a87ff685.png)
  
  ***CASA IoT:***
   En este caso manejamos una red LAN de uso doméstico, por lo que los requerimientos de hardware es menor. Sin embargo, esta casa tiene conectado a tu red LAN una serie de dispositivos IoT (Lámparas inteligentes, puertas, ventanas, cámaras de seguridad, etc). Para conectar esa cantidad de dispositivos a la misma red LAN se hace uso de una Home Gateway, cuya IP es configurada automáticamente mediante DHCP, este recibe la señal inálambrica de los dispositivos IoT y la dirige al router principal de la casa mediante un cable de cobre. Además, la compuerta también está conectada a los dispositivos de los residentes de varias formas; tenemos u smartphone conectado de forma inálambrica y un PC conectado de dforma alámbrica, esto cin el fin de controlar los dispositivos desde estos End Devices.
   
   ![image](https://user-images.githubusercontent.com/89588991/198388334-cc37dfff-c428-4ee4-91e0-091f6ab82bab.png)
  
  ***SERVIDORES:***
   Esta ubicación contiene dos servidores: 
   
   ![image](https://user-images.githubusercontent.com/89588991/198388801-9783d938-ebd2-49d1-ba24-148575a3501f.png)
   
   Uno está configurado para ser un servidor DHCP con dirección incial 209.175.104.0 y máscara de subred 255.255.255.224, además de un límite de ususarios de 31 sin contar las direcciones broadcast y de enrutamiento: 
   
   ![image](https://user-images.githubusercontent.com/89588991/198395367-d3313b73-6a00-4e2e-a625-1f76dc20202a.png)
 
 Además también tenemos otro servidor que es configurado para brinder servicios DNS. La página que este provee es jhs.net:
 
 ![image](https://user-images.githubusercontent.com/89588991/198395895-2fd1b791-5921-4c7b-8fad-09860213db98.png)

Al ingresar a la página desde cualquier End Device en el sistema de redes este es la página final. Para confirmar que las redes están conectadas correctamente, todos los End Devices deben de ser capaces de poder entrar a la página web.

![image](https://user-images.githubusercontent.com/89588991/198397590-fb6a437a-2576-4493-a460-d6ea5bb775d2.png)


#### ANÁLISIS:

1. Desde el Campus podemos ver que la red tiene un camino eficiente hacia el router principal, para confirmar esto se envía un paquete a este mismo router que responde con otro paquete; la señal es de tipo DNS para asegurar su correcta conectividad.

![image](https://user-images.githubusercontent.com/89588991/198402555-4d452edc-4baf-459b-bd23-b7e353427ef9.png)

![image](https://user-images.githubusercontent.com/89588991/198402566-4f11dbbd-a42b-4964-92ab-717ca7e163cd.png)

![image](https://user-images.githubusercontent.com/89588991/198402956-599805be-5aa3-476c-9825-482a009097dc.png)


Posteriormente se envía un paquete mediante TCP para que el servidor correspondiente envíe una respuesta que así mismo verifica el camino que recorres el paquete previo a realizar la conectividad de clinte/servidor.

![image](https://user-images.githubusercontent.com/89588991/198402918-5d1a7824-a483-47e4-b271-f300104e26d6.png)

![image](https://user-images.githubusercontent.com/89588991/198402933-7f926286-610d-444c-856d-bbf394093038.png)

Para verificar la finalización de la conectividad se realiza una petición HTTP.

![image](https://user-images.githubusercontent.com/89588991/198403037-e129d4dc-681c-4e39-9420-3314a95e9809.png)

2. Desde la oficina se inicia con un protocolo ARP para buscar la dirección del servidor en el cual se encuentra alojada la página web, estos paquetes se envían en dirección al router para que este último devuelva la dirección solicitada (191.64.4.2). Posteriormente se hace uso del protocolo DNS y TCP para finiquitar la conexión cliente/servidor, esto recorriedo siempre el camino del dispositivo, al switch, al router primario de la oficina y finalmente se enruta a esas direcciones.

![image](https://user-images.githubusercontent.com/89588991/198415606-52e75ae4-d18a-484e-999c-cba2a34f3a4c.png)

![image](https://user-images.githubusercontent.com/89588991/198415646-377e34ed-5365-4e6f-a4c3-1afa4fcb017e.png)

![image](https://user-images.githubusercontent.com/89588991/198415650-fa85e3fb-08e7-4fa1-b219-8f5dc6d1b423.png)

![image](https://user-images.githubusercontent.com/89588991/198415659-bd61fd1a-6c0a-4a5f-83c0-dc34823e2615.png)

3. Para que los dispositivos finales en la casa inteligente sean capaces de controlar los dispositivos con capacidades IoT se necesitan sus respectivas direcciones IP, para esto se envía un paquete con protocolo ARP que al ser broadcast devolverá como respuesta la respectiva dirección de cada dispositivo conectado en esa red doméstica.

![image](https://user-images.githubusercontent.com/89588991/198416065-57e140d1-912b-4c47-9ef0-e0da02ca856a.png)

Posteriormente se realizan múltiples protocolos TCP con la finalidad de conectarlos entre si, para continuar con la implemencación de IoT TCP el cual finalizará la identificación de dispositivos. 

![image](https://user-images.githubusercontent.com/89588991/198416308-63e5527c-219e-4220-a48d-a9b64b0762b7.png)

![image](https://user-images.githubusercontent.com/89588991/198416318-8e5d320d-485f-49d1-836e-df99bb10bd06.png)

El protocolo ARP al ser broadcast solo recibe una respuesta por envío, es decir que tiene que enviar múltiples paquetes para obtener las direciones de todos los dispositivos. Por lo que el Home Gateway obtendra las direcciones una a la vez hasta que ya haya completado su tabla de direcciones.

![image](https://user-images.githubusercontent.com/89588991/198416581-d4056def-cd03-47ac-9e15-893fc924ab34.png)

![image](https://user-images.githubusercontent.com/89588991/198416619-fed25023-9d5e-44cf-b893-e837c33cd9b4.png)

Finalmente, para verificar la correcta conectividad de la red LAN con IoT, es necesario confirmar que los dispositivos con dicha capacidad puedan ser controlados desde un dispositivo final, por lo que se accede al smatphone para posteriormente dirigirse al apartado de desktop y acceder a la opcion IoT monitor, aquí se deberán obervar que todos los dispositivos IoT están conectados y su utilidad es totalmente funcional desde dicho monitor.

![image](https://user-images.githubusercontent.com/89588991/198416913-a718d7b4-eef5-445e-9f59-f09a48a32e14.png)

4. ***PROGRAMMING:*** Desde la parte del cliente es necesario tener la IP del servidor clara para poder enviar los mensajes satisfactioriamente. El script, además de lo anterior, verifica la correcta conexión de la IP con el servidor. 

![image](https://user-images.githubusercontent.com/89588991/198417223-7659ec2f-ffc0-4ecd-955c-1b10f301397b.png)

El funcionamiento del script es el siguiente: 

- El client envía un paquete a la dirección del servidor con un mensaje ("hello") que va unido a una cadena de carácteres String el cual representa un contador que irá aumentado conforme más paquetes sean enviados. 
- En el momento en el que el script es ejecutado en el servidor, este compara los datos enviados por el client.
- Si el client.remoteIP coincide con la dirección previamente guardada, el servidor accede al paquete.
- El servidor devuelve una respuesta al client con un nuevo mensaje evidenciando que si se recibió el primer paquete.

![image](https://user-images.githubusercontent.com/89588991/198417688-f7c2edd1-eda2-462e-97bb-6656801fd7d8.png)

![image](https://user-images.githubusercontent.com/89588991/198418004-5ae5c85a-b79e-411b-8844-403349d87ba0.png)

![image](https://user-images.githubusercontent.com/89588991/198418013-74f7d558-37f6-4249-95fd-cb591b5fc3e6.png)

Este es el código usado en cuestión con archivo en formato .txt para la comodidad del sitio.

[Configuraciones.txt](https://github.com/RoryRoth/Final_Project_Redes/files/9883735/Configuraciones.txt)

FInalmente, para una explicación más concisa por favor revisar el video presentado a continuación:

https://www.youtube.com/watch?v=lTVH18dPtvE

