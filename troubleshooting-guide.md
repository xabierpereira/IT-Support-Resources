# 🔧 Guía de Troubleshooting Técnico IT

## Metodología de resolución de problemas

### 1. Identificar el problema
- Escuchar activamente al usuario
- Hacer preguntas específicas
- Reproducir el error si es posible
- Documentar síntomas exactos

### 2. Recopilar información
```bash
# Windows - Información del sistema
systeminfo
wmic computersystem get model,name,manufacturer
dxdiag

# Linux - Información del sistema
uname -a
lsb_release -a
cat /proc/cpuinfo
cat /proc/meminfo
```

### 3. Análizar posibles causas
- Hardware vs Software
- Reciente vs Persistente
- Local vs Red
- Usuario específico vs Global

---

## 🖥️ Problemas comunes Windows

### Problema: PC lento
**Diagnóstico:**
```cmd
# Verificar uso CPU/RAM
taskmgr

# Verificar inicio automático
msconfig → Startup

# Verificar espacio disco
wmic logicaldisk get size,freespace,caption

# Verificar fragmentación (HDD)
defrag C: /A
```

**Soluciones:**
1. Deshabilitar programas inicio innecesarios
2. Limpiar archivos temporales: `cleanmgr`
3. Verificar malware: Windows Defender scan
4. Actualizar drivers
5. Upgrade RAM/SSD si es limitación hardware

---

### Problema: No hay conexión a Internet
**Diagnóstico:**
```cmd
# Verificar conectividad básica
ping 8.8.8.8
ping google.com

# Verificar configuración IP
ipconfig /all

# Renovar IP
ipconfig /release
ipconfig /renew

# Limpiar caché DNS
ipconfig /flushdns

# Verificar ruta a destino
tracert google.com

# Reset completo red
netsh winsock reset
netsh int ip reset
```

**Soluciones:**
1. Verificar cable ethernet conectado
2. Verificar WiFi activado
3. Reiniciar router/modem
4. Actualizar drivers tarjeta red
5. Deshabilitar/habilitar adaptador red
6. Configurar DNS manualmente (8.8.8.8, 1.1.1.1)

---

### Problema: Pantalla azul (BSOD)
**Diagnóstico:**
```cmd
# Ver código error en pantalla azul
# Buscar archivo minidump
C:\Windows\Minidump

# Herramienta: BlueScreenView (Nirsoft)
# Analizar dump files

# Verificar memoria RAM
mdsched.exe
```

**Causas comunes:**
- Driver corrupto/incompatible
- Hardware defectuoso (RAM, HDD)
- Overheating
- Actualización Windows problemática

---

### Problema: No arranca Windows
**Diagnóstico:**
1. Verificar POST (pantalla BIOS aparece?)
2. Verificar boot order en BIOS
3. Intentar Safe Mode: F8 al arrancar
4. Usar Windows Recovery Environment

**Soluciones:**
```cmd
# Desde Recovery Console:
bootrec /fixmbr
bootrec /fixboot
bootrec /rebuildbcd

# Reparar archivos sistema
sfc /scannow

# Restaurar punto anterior
rstrui.exe
```

---

## 🐧 Problemas comunes Linux

### Problema: Sistema no arranca
**Diagnóstico:**
```bash
# Boot en recovery mode
# Verificar filesystem
fsck /dev/sda1

# Verificar GRUB
grub-install /dev/sda
update-grub
```

---

### Problema: Permisos denegados
**Diagnóstico:**
```bash
# Ver permisos
ls -la

# Ver propietario
stat archivo.txt

# Verificar usuario actual
whoami
id
```

**Soluciones:**
```bash
# Cambiar permisos
chmod 755 archivo
chmod u+x script.sh

# Cambiar propietario
chown usuario:grupo archivo

# Ejecutar con sudo si es necesario
sudo comando
```

---

### Problema: Servicio no inicia
**Diagnóstico:**
```bash
# Verificar estado servicio
systemctl status nombre-servicio

# Ver logs
journalctl -u nombre-servicio
tail -f /var/log/syslog
```

**Soluciones:**
```bash
# Reiniciar servicio
systemctl restart nombre-servicio

# Habilitar al inicio
systemctl enable nombre-servicio

# Verificar configuración
nombre-servicio -t  # test config
```

---

## 🌐 Problemas de red

### Verificar conectividad capa por capa

**Capa 1 - Física:**
- Cable conectado?
- LED encendido tarjeta red?
- Cable correcto (straight vs crossover)?

**Capa 2 - Enlace:**
```bash
# Ver interfaces
ip link show      # Linux
ipconfig          # Windows

# Verificar MAC address
ip link show eth0
getmac           # Windows
```

**Capa 3 - Red:**
```bash
# Verificar IP asignada
ip addr show     # Linux
ipconfig         # Windows

# Verificar gateway
ip route         # Linux
route print      # Windows

# Ping gateway
ping 192.168.1.1
```

**Capa 4-7 - Transporte/Aplicación:**
```bash
# Verificar puertos abiertos
netstat -tulpn   # Linux
netstat -ano     # Windows

# Test puerto específico
telnet google.com 80
nc -zv google.com 443
```

---

## 🛠️ Herramientas imprescindibles

### Windows
- **Process Explorer** (Sysinternals): Gestor procesos avanzado
- **Autoruns** (Sysinternals): Ver todo que arranca
- **CrystalDiskInfo**: Estado discos duros
- **HWiNFO**: Info hardware completa
- **Malwarebytes**: Anti-malware
- **Recuva**: Recuperación archivos
- **TreeSize**: Analizar espacio disco

### Linux
- **htop**: Monitor recursos
- **iotop**: Monitor I/O disco
- **iftop**: Monitor red
- **netstat/ss**: Conexiones red
- **tcpdump**: Captura paquetes
- **strace**: Debug procesos
- **lsof**: Archivos abiertos

---

## 📋 Checklist soporte remoto

Antes de conectar:
- [ ] Obtener permiso usuario
- [ ] Confirmar problema reportado
- [ ] Backup datos importantes si aplica

Durante sesión:
- [ ] Explicar cada paso al usuario
- [ ] No tocar archivos personales sin permiso
- [ ] Documentar cambios realizados

Después sesión:
- [ ] Verificar problema resuelto
- [ ] Explicar qué se hizo y por qué
- [ ] Prevención: cómo evitar futuro
- [ ] Documentar caso para base conocimientos

---

## 💡 Mejores prácticas

1. **Siempre haz backup antes de cambios importantes**
2. **Documenta todo** (qué funcionaba, qué hiciste, resultado)
3. **Google es tu amigo** (pero verifica fuentes)
4. **No adivines** - si no sabes, investiga o escala
5. **Comunica claramente** con el usuario
6. **Mantén calma** incluso si el usuario está frustrado
7. **Aprende de cada caso** - crea tu base de conocimientos

---

## 📚 Recursos útiles

- **Microsoft Docs**: docs.microsoft.com
- **Linux man pages**: man7.org
- **Stack Overflow**: stackoverflow.com
- **Reddit r/sysadmin**: reddit.com/r/sysadmin
- **Spiceworks Community**: community.spiceworks.com

---

**Autor:** Xabier Pereira  
**Última actualización:** Febrero 2026  
**Licencia:** MIT
