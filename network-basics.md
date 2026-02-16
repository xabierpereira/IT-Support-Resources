# 🌐 Fundamentos de Redes - Guía Rápida

## Modelo OSI (7 capas)

```
7. APLICACIÓN  → HTTP, FTP, SMTP, DNS
6. PRESENTACIÓN → SSL/TLS, JPEG, ASCII
5. SESIÓN      → NetBIOS, RPC
4. TRANSPORTE  → TCP, UDP
3. RED         → IP, ICMP, OSPF
2. ENLACE      → Ethernet, WiFi, Switch
1. FÍSICA      → Cables, hubs, señales
```

### Mnemotécnica: **A**ll **P**eople **S**eem **T**o **N**eed **D**ata **P**rocessing

---

## Modelo TCP/IP (4 capas)

```
4. APLICACIÓN  → HTTP, DNS, FTP, SSH
3. TRANSPORTE  → TCP, UDP
2. INTERNET    → IP, ICMP, ARP
1. ACCESO RED  → Ethernet, WiFi
```

---

## 📍 Direccionamiento IP

### IPv4 - Clases

| Clase | Rango | Uso |
|-------|-------|-----|
| A | 1.0.0.0 - 126.255.255.255 | Redes muy grandes |
| B | 128.0.0.0 - 191.255.255.255 | Redes medianas |
| C | 192.0.0.0 - 223.255.255.255 | Redes pequeñas |
| D | 224.0.0.0 - 239.255.255.255 | Multicast |
| E | 240.0.0.0 - 255.255.255.255 | Experimental |

### Direcciones privadas (RFC 1918)

```
10.0.0.0/8        → 10.0.0.0 - 10.255.255.255
172.16.0.0/12     → 172.16.0.0 - 172.31.255.255
192.168.0.0/16    → 192.168.0.0 - 192.168.255.255
```

### Direcciones especiales

```
127.0.0.1         → Loopback (localhost)
0.0.0.0           → Red actual
255.255.255.255   → Broadcast
169.254.0.0/16    → APIPA (auto-config cuando no hay DHCP)
```

---

## 🔢 Subnetting

### Subnet Masks comunes

| CIDR | Máscara | Hosts útiles |
|------|---------|--------------|
| /8 | 255.0.0.0 | 16,777,214 |
| /16 | 255.255.0.0 | 65,534 |
| /24 | 255.255.255.0 | 254 |
| /25 | 255.255.255.128 | 126 |
| /26 | 255.255.255.192 | 62 |
| /27 | 255.255.255.224 | 30 |
| /28 | 255.255.255.240 | 14 |
| /29 | 255.255.255.248 | 6 |
| /30 | 255.255.255.252 | 2 |

### Cálculo rápido subnetting

**Ejemplo:** 192.168.1.0/26

```
1. Máscara: /26 = 255.255.255.192
2. Bits host: 32 - 26 = 6 bits
3. Hosts por subred: 2^6 - 2 = 62 hosts
4. Número subredes: 2^2 = 4 (usamos 2 bits para subred)
5. Incremento: 256 - 192 = 64

Subredes:
- 192.168.1.0/26   → 192.168.1.1 - 192.168.1.62
- 192.168.1.64/26  → 192.168.1.65 - 192.168.1.126
- 192.168.1.128/26 → 192.168.1.129 - 192.168.1.190
- 192.168.1.192/26 → 192.168.1.193 - 192.168.1.254
```

---

## 🔌 Protocolos de capa de transporte

### TCP (Transmission Control Protocol)

**Características:**
- Orientado a conexión (3-way handshake)
- Confiable (retransmisión si hay pérdida)
- Ordenado (paquetes en orden)
- Control de flujo
- Más lento que UDP

**Usos:** HTTP, HTTPS, FTP, SSH, Email

**3-Way Handshake:**
```
Cliente → SYN → Servidor
Cliente ← SYN-ACK ← Servidor
Cliente → ACK → Servidor
[Conexión establecida]
```

### UDP (User Datagram Protocol)

**Características:**
- Sin conexión
- No confiable (sin retransmisión)
- Sin orden garantizado
- Sin control de flujo
- Más rápido que TCP

**Usos:** DNS, DHCP, VoIP, streaming video, gaming

---

## 🌍 Protocolos comunes

### DNS (Domain Name System)
- **Puerto:** 53 UDP/TCP
- **Función:** Traduce nombres dominio a IPs
- **Ejemplo:** google.com → 142.250.185.46

```bash
# Consultar DNS
nslookup google.com
dig google.com
host google.com
```

### DHCP (Dynamic Host Configuration Protocol)
- **Puertos:** 67 (servidor), 68 (cliente) UDP
- **Función:** Asigna IPs automáticamente
- **Proceso DORA:**
  1. **D**iscover - Cliente busca servidor DHCP
  2. **O**ffer - Servidor ofrece IP
  3. **R**equest - Cliente solicita IP ofrecida
  4. **A**ck - Servidor confirma asignación

### HTTP/HTTPS
- **Puertos:** 80 (HTTP), 443 (HTTPS)
- **Función:** Transferencia hipertexto web

### FTP (File Transfer Protocol)
- **Puertos:** 20 (datos), 21 (control)
- **Función:** Transferencia archivos

### SSH (Secure Shell)
- **Puerto:** 22
- **Función:** Acceso remoto seguro

### Telnet
- **Puerto:** 23
- **Función:** Acceso remoto NO seguro (obsoleto)

### SMTP (Simple Mail Transfer Protocol)
- **Puerto:** 25, 587 (TLS)
- **Función:** Envío email

### POP3 / IMAP
- **Puertos:** 110 (POP3), 143 (IMAP)
- **Función:** Recepción email

---

## 🔧 Comandos de red esenciales

### Windows

```cmd
:: Ver configuración IP
ipconfig
ipconfig /all

:: Renovar IP DHCP
ipconfig /release
ipconfig /renew

:: Limpiar caché DNS
ipconfig /flushdns

:: Mostrar tabla ARP
arp -a

:: Ver tabla routing
route print

:: Agregar ruta estática
route add 192.168.2.0 mask 255.255.255.0 192.168.1.1

:: Ver conexiones activas
netstat -ano
netstat -b  # muestra programas

:: Test conectividad
ping 8.8.8.8
ping -t google.com  # continuo

:: Rastrear ruta
tracert google.com

:: Escanear puerto
telnet google.com 80

:: Ver adaptadores de red
getmac /v
```

### Linux

```bash
# Ver configuración IP
ip addr show
ifconfig

# Ver tabla routing
ip route show
route -n

# Ver tabla ARP
ip neigh show
arp -a

# Renovar IP DHCP
sudo dhclient -r  # release
sudo dhclient     # renew

# Ver conexiones
netstat -tulpn
ss -tulpn

# Test conectividad
ping -c 4 8.8.8.8

# Rastrear ruta
traceroute google.com

# Escanear puertos
nmap -sT -p 1-1000 192.168.1.1

# Capturar tráfico
sudo tcpdump -i eth0

# Ver DNS config
cat /etc/resolv.conf

# Test DNS
dig google.com
nslookup google.com
```

---

## 🔐 Seguridad de red básica

### Firewalls

**Tipos:**
- **Packet filtering:** Filtra por IP, puerto, protocolo
- **Stateful:** Rastrea estado conexiones
- **Application layer:** Inspecciona contenido aplicación

### NAT (Network Address Translation)

**Función:** Traduce IPs privadas → IP pública

**Tipos:**
- **SNAT:** Source NAT (salida internet)
- **DNAT:** Destination NAT (port forwarding)
- **PAT:** Port Address Translation (NAT overload)

### VPN (Virtual Private Network)

**Protocolos:**
- **PPTP:** Antiguo, inseguro
- **L2TP/IPsec:** Más seguro
- **OpenVPN:** Open source, muy seguro
- **WireGuard:** Moderno, rápido

---

## 📶 Redes Inalámbricas

### Estándares WiFi

| Estándar | Nombre | Frecuencia | Velocidad máx |
|----------|--------|------------|---------------|
| 802.11b | - | 2.4 GHz | 11 Mbps |
| 802.11g | - | 2.4 GHz | 54 Mbps |
| 802.11n | WiFi 4 | 2.4/5 GHz | 600 Mbps |
| 802.11ac | WiFi 5 | 5 GHz | 3.5 Gbps |
| 802.11ax | WiFi 6 | 2.4/5/6 GHz | 9.6 Gbps |

### Seguridad WiFi

| Protocolo | Seguridad | Estado |
|-----------|-----------|--------|
| WEP | Muy baja | Obsoleto ❌ |
| WPA | Baja | Obsoleto ❌ |
| WPA2 | Buena | Aceptable ⚠️ |
| WPA3 | Excelente | Recomendado ✅ |

---

## 🛠️ Dispositivos de red

### Hub
- Capa 1 (física)
- Repite señal a todos los puertos
- Colisiones frecuentes
- **Obsoleto** ❌

### Switch
- Capa 2 (enlace)
- Envía tráfico solo al puerto destino
- Usa tabla MAC addresses
- **Estándar actual** ✅

### Router
- Capa 3 (red)
- Enruta entre redes diferentes
- Usa tabla routing
- **Esencial** ✅

### Access Point
- Capa 2
- Proporciona conectividad WiFi
- Conectado a switch/router

### Firewall
- Capa 3-7
- Filtra tráfico según reglas
- Protección seguridad

---

## 📊 Troubleshooting de red

### Metodología

```
1. ¿Hay link físico?
   → Verificar cable, LEDs

2. ¿Tiene IP?
   → ipconfig / ip addr

3. ¿Puede hacer ping a gateway?
   → ping 192.168.1.1

4. ¿Puede hacer ping a internet?
   → ping 8.8.8.8

5. ¿Funciona DNS?
   → ping google.com

6. ¿Puerto/servicio accesible?
   → telnet/nc test
```

### Comandos diagnóstico orden

```bash
# 1. Verificar interfaz física
ip link show

# 2. Verificar IP asignada
ip addr show

# 3. Verificar gateway
ip route | grep default

# 4. Test gateway
ping -c 4 [gateway_ip]

# 5. Test DNS público
ping -c 4 8.8.8.8

# 6. Test resolución DNS
ping -c 4 google.com

# 7. Test puerto específico
telnet google.com 80
```

---

## 📚 Recursos adicionales

- **SubnetCalc:** www.subnet-calculator.com
- **Cisco Packet Tracer:** Simulador redes
- **Wireshark:** Análisis de paquetes
- **RFC Index:** www.rfc-editor.org

---

**Autor:** Xabier Pereira  
**Última actualización:** Febrero 2026  
**Licencia:** MIT
