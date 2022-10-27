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

![image](https://user-images.githubusercontent.com/89588991/198400741-48f16590-818e-4ead-9699-9298eb80f332.png)










