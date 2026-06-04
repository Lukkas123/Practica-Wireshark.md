# Análisis de Tráfico de Red con Wireshark

## Descripción

Esta práctica consiste en la captura y análisis de tráfico de red utilizando Wireshark para examinar paquetes ICMP, TCP e IP, comprender el funcionamiento de protocolos fundamentales y evaluar sus implicancias en la seguridad informática.

## Objetivos

* Capturar tráfico de red utilizando Wireshark.
* Analizar mensajes ICMP Echo Request y Echo Reply.
* Comprender el proceso de establecimiento de conexiones TCP.
* Observar la fragmentación de paquetes IP.
* Identificar riesgos de seguridad asociados a distintos protocolos.

---

## Herramientas Utilizadas

* Wireshark
* Windows/Linux
* Ping
* Navegador Web

---

## Archivos de Captura

| Archivo             | Descripción                  |
| ------------------- | ---------------------------- |
| `ping_icmp.pcapng`  | Captura de tráfico ICMP      |
| `http_https.pcapng` | Captura de tráfico TCP/HTTPS |

---

## Análisis ICMP

### Filtro Aplicado

```wireshark
icmp
```

### Actividad Realizada

Se ejecutó un ping hacia un host externo para generar tráfico ICMP.

```bash
ping 8.8.8.8
```

### Campos Analizados

* Echo Request
* Echo Reply
* Type
* Code
* Checksum
* Identifier
* Sequence Number
* TTL

## Análisis del Handshake TCP

### Filtro Aplicado

```wireshark
tcp.port == 443
```

### Secuencia Observada

1. SYN
2. SYN-ACK
3. ACK

### Flags TCP

| Etapa   | Descripción                    |
| ------- | ------------------------------ |
| SYN     | Inicio de conexión             |
| SYN-ACK | Confirmación del servidor      |
| ACK     | Confirmación final del cliente |

## Análisis de Fragmentación IP

### Generación de Tráfico

Linux/MacOS:

```bash
ping -s 1000 8.8.8.8
```

Windows:

```cmd
ping -l 1000 8.8.8.8
```

### Filtro Aplicado

```wireshark
ip.frag_offset > 0
```

### Observaciones

* Identificación de paquetes IP fragmentados.
* Análisis del Fragment Offset.
* Verificación de la bandera More Fragments (MF).

## Reflexión de Seguridad

### Riesgos de ICMP

* Reconocimiento de red.
* Descubrimiento de hosts.
* Ataques de inundación ICMP (ICMP Flood).

### Riesgos de HTTP

* Comunicación sin cifrado.
* Exposición de credenciales.
* Intercepción de información sensible.

### Amenazas Relacionadas

#### Sniffing

Captura e inspección no autorizada del tráfico de red.

#### Replay Attack

Reenvío de paquetes previamente capturados para reproducir una comunicación legítima.

#### Denial of Service (DoS)

Agotamiento de recursos mediante la generación masiva de tráfico.

---

## Conocimientos Aplicados

* TCP/IP
* ICMP
* Handshake TCP
* Fragmentación IP
* Análisis de Paquetes
* Wireshark
* Seguridad de Redes
* Inspección de Tráfico
* Análisis de Protocolos

---

