 Wireshark Packet Analysis Lab
 Descripción

Práctica de análisis de tráfico de red utilizando Wireshark para capturar y examinar paquetes ICMP, TCP e IP, comprendiendo el funcionamiento de protocolos fundamentales y su relación con la seguridad informática.

 Objetivos
Capturar tráfico de red utilizando Wireshark.
Analizar mensajes ICMP Echo Request y Echo Reply.
Comprender el proceso de establecimiento de conexiones TCP.
Observar la fragmentación de paquetes IP.
Identificar riesgos de seguridad asociados a distintos protocolos.
 Herramientas Utilizadas
Wireshark
Sistema Operativo Windows/Linux
Ping
Navegador Web
 Archivos de Captura
Archivo	Descripción
ping_icmp.pcapng	Captura de tráfico ICMP
http_https.pcapng	Captura de tráfico TCP/HTTPS
 Análisis ICMP
Filtro aplicado
icmp
Actividad realizada

Se ejecutó un ping hacia un host externo para generar tráfico ICMP.

ping 8.8.8.8
Aspectos analizados
Echo Request
Echo Reply
Type
Code
Checksum
Identifier
Sequence Number
TTL
Captura




 Análisis del Handshake TCP
Filtro aplicado
tcp.port == 443
Secuencia observada
SYN
SYN-ACK
ACK
Flags TCP
Etapa	Flags
SYN	Inicio de conexión
SYN-ACK	Confirmación del servidor
ACK	Confirmación final del cliente
Captura




 Fragmentación IP
Generación de tráfico

Linux/macOS:

ping -s 1000 8.8.8.8

Windows:

ping -l 1000 8.8.8.8
Filtro utilizado
ip.frag_offset > 0
Observaciones
Identificación de fragmentos IP.
Análisis de Fragment Offset.
Verificación de la bandera More Fragments (MF).
Captura




 Reflexión de Seguridad
Riesgos de ICMP
Reconocimiento de red.
Enumeración de hosts.
Ataques de ICMP Flood.
Riesgos de HTTP
Transmisión sin cifrado.
Exposición de credenciales.
Intercepción de datos sensibles.
Amenazas Relacionadas
Sniffing

Captura e inspección no autorizada de tráfico de red.

Replay Attack

Reenvío de paquetes previamente capturados para intentar reproducir una comunicación válida.

Denial of Service (DoS)

Saturación de recursos mediante grandes volúmenes de tráfico.

 Conocimientos Aplicados
TCP/IP
ICMP
TCP Handshake
Fragmentación IP
Análisis de Paquetes
Wireshark
Network Security
Traffic Inspection
Packet Analysis
