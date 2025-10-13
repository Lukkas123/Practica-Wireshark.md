Ejercicio 1 WireShark análisis de captura de paquetes 

1. Captura de tráfico o Abrí Wireshark y seleccioná tu interfaz de red. o Aplicá un filtro para ICMP (icmp). o Hacé un ping a un host (ej: 8.8.8.8 o un servidor local). o Guardá la captura como ping_icmp.pcapng. 

2. Análisis del ICMP o Identificá el paquete Echo Request y el Echo Reply. o ¿Qué campos podés observar en el encabezado ICMP? o ¿Cuál es el TTL del paquete de respuesta? ¿Qué significa? 

3. Captura de protocolo TCP o Generá tráfico HTTP o HTTPS visitando una web. o Aplicá un filtro tcp.port == 80 (o tcp.port == 443). o Guardá como http_https.pcapng. 

4. Análisis del Handshake TCP o Localizá la secuencia SYN → SYN-ACK → ACK. o ¿Qué significan los flags en cada etapa? o ¿Cuál fue el número de secuencia inicial? 

5. Inyección de ruido o Usá ping -s 1000 (Linux/macOS) o ping -l 1000 (Windows) para mandar paquetes grandes. o Capturá de nuevo y analizá cómo se fragmentan en IP (filtro: ip.frag_offset > 0). o ¿Qué riesgo puede representar la fragmentación en ataques DoS? 

6. Reflexión de seguridad o Explicá por qué protocolos como ICMP o HTTP pueden ser problemáticos si no se controlan. o Relacioná con amenazas reales: ▪ Sniffing (confidencialidad = 0) ▪ Replay (paquetes repetidos) ▪ DoS (inundación ICMP)

Ejercicio 2 Direcciones IP Este modelo deberá estar configurado en Packet Tracer. Se les pedirá en forma virtual a cada equipo que muestran la configuración funcionando mediante un ping interno entre las PC, dentro de la evaluación del trabajo. Dirección a ser asignado Red 192.168.25.0 Máscara 255.255.255.0 Sub-red A 30 direcciones IP Sub-red B 14 direcciones IP

Ejercicio 1

2- En el encabezado ICMP se puede observar los campos frame, ethernet, internet protocol e internet control message protocol (ICMP)

<img width="603" height="236" alt="image" src="https://github.com/user-attachments/assets/ae441ffb-0fe6-40b6-9ebb-153bfdff9005" />



El TTL de respuesta es 255, es los saltos que puede dar el paquete de router en router antes que sea descartado cuando llegue a 0

<img width="276" height="18" alt="image" src="https://github.com/user-attachments/assets/4ee7237a-6d5e-41bc-959d-019da734e282" />



4- Las flags en cada etapa significa:
SYN= Iniciar una conexión TCP
ACK= Indicar que un paquete fue entregado correctamente
Fin= Cerrar una conexión TCP
Push= Le dice al receptor que entregue los datos inmediatamente
Reset= Reiniciar o cerrar una conexión 
Urgent= . Los datos son urgentes y deben priorizarse
Explicit Congestion Notification echo= Indicar que el paquete entrante tenía ECN marcado y que se debe informar de congestión.
Congestion Window Reduced: Indica que el emisor ha reducido su ventana de congestión en respuesta a la señal ECN echo.
ECN echo = Indica congestión en la red
Accurate ECN= Manejo de congestión mejorada de ECN

El número de secuencia inicial fue 0

<img width="518" height="303" alt="image" src="https://github.com/user-attachments/assets/7ce17f9e-5a58-4bd0-9a37-085b7ef6d7fc" />



5- Con ip -s 2000 al servidor dns de google se superó el MTU de la red por lo que se fragmentó y se vio lo siguiente:
Esto representa un peligro ya que se puede hacer un ataque DoS al inundar de paquetes la red y en este caso Google ignora paquetes fragmentados ya que no hubo respuesta del servidor

<img width="1206" height="425" alt="image" src="https://github.com/user-attachments/assets/d44befd1-1e69-404c-bffd-2bd2072a4d54" />


6) 
ICMP: Este protocolo de control permite hacer ping a la dirección ip que queramos.  Al mandar paquetes grandes estos se fragmentan y permiten inundar una red y afectar su disponibilidad. Esto sería un ataque de DoS simple de hacer que no requiere muchos conocimientos técnicos. 
HTTP: Permite el sniffeo de los datos transmitidos por la red por lo que afecta la confidencialidad de la información. En este protocolo se podría hacer replay al reenviar un pago, una orden o un token de autenticación antiguo para acceder sin autorización.
