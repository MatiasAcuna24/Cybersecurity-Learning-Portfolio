# OSI Model Notes

## 1. What is the OSI Model?

El modelo OSI es un marco de referencia que divide la comunicación entre dispositivos en 7 capas. Esto con la intención de poder entender a mayor grado cómo funciona el viaje de la información desde que el cliente mediante un software, navegador web, inicia un evento y este viaja a través de las 7 capas hasta llegar al dispositivo receptor que sería el destino final.

* **What does OSI mean?**

R: Open System Interconnection (Modelo de interconexión de sistemas abiertos)

* **Why was this model created?**

R: Para ayudar a tener un mejor entendimiento de cómo funciona la comunicación entre dispositivos. Tener una estandarización de cómo se tienen que comunicar correctamente los dispositivos y una mejor interoperabilidad.

* **What is it used for in networking?**

R: Sirve para tener un mayor entendimiento de la comunicación, de las aplicaciones en las cuales se inicia la comunicación (Capa 7), la manera en la que se presentan los datos (Capa 6), cómo se mantiene la sesión entre dispositivos (Capa 5), el transporte de la información mediante los protocolos TCP/UDP y sus distintos puertos de comunicación (Capa 4), el enrutamiento y las direcciones IP (Capa 3), el enlace de los datos dentro de la red local (Capa 2), y por último la capa física (Capa 1) donde viaja la información principalmente (Cable Ethernet, Fibra Óptica, WiFi).

* **How does it help diagnose connectivity problems?**

R: Ayuda a identificar con mayor claridad en qué parte del proceso de comunicación está ocurriendo un problema de conectividad, permitiendo aplicar una solución más eficiente.

---

## 2. OSI Model Layers

El modelo OSI divide la comunicación de red en siete capas.

---

### Layer 1 – Physical

**Function**

Aquí se envían los bits en 0 y 1. Esto ocurre en medios físicos como:

* cable Ethernet
* fibra óptica
* redes WiFi

**My Notes**

* Trabaja con señales eléctricas, ópticas o radiofrecuencia
* No interpreta información, solo transmite bits

Problemas comunes en esta capa:

* cable desconectado
* cable dañado
* interferencia WiFi
* puerto defectuoso en switch o router

---

### Layer 2 – Data Link

**Function**

Aquí ocurre la conexión entre dispositivos dentro de la misma red local.

**Important Concepts**

* dirección MAC
* comunicación dentro de la red local

**My Notes**

* Cada dispositivo tiene una dirección MAC única
* Esta capa es gestionada principalmente por switches

Protocolos importantes:

* ARP (Address Resolution Protocol)

ARP permite traducir una dirección IP a una dirección MAC.

Ejemplo:

IP → 192.168.1.10  
MAC → 00:1A:2B:3C:4D:5E

Problemas comunes:

* ARP Spoofing
* loops de red
* problemas de switching

---

### Layer 3 – Network

**Function**

Aquí ocurre el enrutamiento y redirección de direcciones IP hacia el destino final.

**Important Concepts**

* direccionamiento IP
* enrutamiento de paquetes

**My Notes**

Protocolos importantes:

* IP
* ICMP
* IPsec

Herramientas comunes:

* ping
* traceroute
* ipconfig / ifconfig

Problemas comunes:

* IP incorrecta
* gateway incorrecto
* problemas de routing

Esta capa permite que los datos viajen entre distintas redes, lo que hace posible el funcionamiento de Internet.

---

### Layer 4 – Transport

**Function**

Aquí se transportan los datos utilizando protocolos como TCP (Transmission Control Protocol) o UDP (User Datagram Protocol) junto con los distintos puertos de comunicación.

Ejemplos de puertos TCP:

* 21 FTP
* 22 SSH
* 23 Telnet
* 25 SMTP
* 53 DNS
* 80 HTTP
* 443 HTTPS
* 3306 MySQL

Ejemplos de puertos UDP:

* 53 DNS
* 67 / 68 DHCP
* 123 NTP
* 161 / 162 SNMP

**Important Protocols**

* TCP (seguro y confiable)
* UDP (más rápido pero menos confiable)

**My Notes**

TCP utiliza el proceso llamado:

**Three Way Handshake**

Pasos:

1. SYN  
2. SYN-ACK  
3. ACK  

Esto permite establecer una conexión confiable.

Estados importantes de TCP:

* LISTEN
* ESTABLISHED
* CLOSE_WAIT
* FIN_WAIT

En ciberseguridad muchos ataques comienzan con **escaneos de puertos** para identificar servicios activos.

Herramienta común:

* Nmap

---

### Layer 5 – Session

**Function**

Aquí se mantienen las sesiones entre dispositivos durante la comunicación.

**My Notes**

Esta capa gestiona:

* inicio de sesión
* mantenimiento de la sesión
* cierre de sesión

---

### Layer 6 – Presentation

**Function**

Aquí se formatean, cifran y preparan los datos para que puedan ser interpretados por el sistema receptor.

**Examples**

* cifrado
* compresión
* formato de datos

**My Notes**

Aquí ocurre:

* cifrado TLS / SSL
* conversión de formatos
* codificación de caracteres

Ejemplos:

* ASCII
* UTF-8
* JPEG
* TLS encryption

Esta capa asegura que los datos enviados por un sistema puedan ser interpretados correctamente por el sistema receptor.

---

### Layer 7 – Application

**Function**

Aquí el usuario inicia la comunicación mediante aplicaciones como navegadores web o software de escritorio.

**Common Protocols**

* HTTP
* DNS
* FTP
* SMTP

**My Notes**

Ejemplos de aplicaciones:

* Chrome
* Firefox
* Outlook
* Thunderbird

Otros protocolos comunes:

* HTTPS
* SSH
* SNMP

Es la capa más cercana al usuario final.

---

## 3. Practical Example

Describe qué ocurre cuando visitas un sitio web.

Ejemplo:

1. El navegador solicita la dirección del sitio.
2. DNS traduce el dominio a una dirección IP.
3. Se establece una conexión TCP.
4. El servidor envía los datos de la página.

**Explanation in My Own Words**

Se inicia la comunicación mediante la capa 7 de aplicación donde el usuario ingresa una dirección HTTP o HTTPS, por ejemplo:

https://www.github.com

Luego se utiliza el protocolo DNS para traducir el dominio a una dirección IP.

Posteriormente se establece la conexión utilizando el **Three-Way Handshake de TCP**:

1. SYN
2. SYN-ACK
3. ACK

Finalmente los datos viajan a través de las capas del modelo OSI hasta llegar a la capa física donde se transmiten mediante cable Ethernet, fibra óptica o WiFi.

---

## 4. Why the OSI Model is Important

El modelo OSI ayuda a:

* entender cómo viajan los datos en una red
* diagnosticar problemas de conectividad
* analizar tráfico de red

**Explanation in My Own Words**

El modelo nos ayuda a entender cómo viajan los datos dentro de una red ya que divide la comunicación en siete capas.

Esto facilita el diagnóstico de fallas, permitiendo identificar en qué parte del proceso ocurre un problema de comunicación.

**My Notes**

En análisis de seguridad se observan principalmente:

* Layer 7 → HTTP / DNS traffic
* Layer 4 → TCP / UDP ports and connections
* Layer 3 → Source and destination IP addresses

---

## 5. Key Concepts to Remember

* La capa que utiliza IP es la **Layer 3 (Network)**
* La capa que utiliza TCP/UDP es la **Layer 4 (Transport)**
* La capa que utilizan las aplicaciones es la **Layer 7 (Application)**

La diferencia entre TCP y UDP es:

* **TCP:** más lento pero confiable (usa Three Way Handshake)
* **UDP:** más rápido pero menos confiable