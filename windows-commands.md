# 🪟 Comandos útiles Windows

---

## 🔌 Diagnóstico de red
```cmd
ipconfig /all                 # Ver configuración de red
ping 8.8.8.8                  # Test de conectividad
tracert google.com            # Trazar ruta a un host
nslookup google.com           # Resolver DNS
netstat -an                   # Ver conexiones de red activas
netsh wlan show profiles      # Listar redes WiFi guardadas
netsh wlan show interface     # Estado de interfaces WiFi
```
## 💻 Información del sistema
```cmd
systeminfo                     # Información general del sistema
msinfo32                       # Información completa (ventana GUI)
taskmgr                        # Administrador de tareas
wmic cpu get name               # Nombre del procesador
wmic memorychip get capacity    # Tamaño de RAM por módulo
wmic bios get serialnumber      # Número de serie de la BIOS
dxdiag                          # Diagnóstico DirectX (GUI)
chkdsk /f                       # Comprobar errores de disco
sfc /scannow                    # Comprobar y reparar archivos del sistema
```
## 📁 Gestión de archivos 
```cmd
dir                  # Listar archivos
cd [carpeta]         # Cambiar directorio
copy [origen] [destino]   # Copiar archivos
move [origen] [destino]   # Mover o renombrar archivos
del [archivo]            # Borrar archivos
mkdir [carpeta]          # Crear nueva carpeta
rmdir /s [carpeta]       # Eliminar carpeta y contenido
attrib +h [archivo]      # Ocultar archivo
```

## 🔹 Comandos rápidos desde Win + R
``` 
msinfo32        # Información del sistema (GUI)
taskmgr         # Administrador de tareas
dxdiag          # Diagnóstico DirectX
compmgmt.msc    # Administración de equipos
devmgmt.msc     # Administrador de dispositivos
services.msc    # Servicios de Windows
eventvwr        # Visor de eventos
control         # Panel de control
cleanmgr        # Liberador de espacio en disco
regedit         # Editor del registro

