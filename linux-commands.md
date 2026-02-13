# 🐧 Comandos útiles Linux

Repositorio personal con **comandos prácticos para Linux**, enfocado en soporte técnico y administración básica.

---

## 🔌 Diagnóstico de red

```bash
ifconfig                       # Mostrar interfaces de red
ip a                            # Ver configuración de red
ping 8.8.8.8                    # Test de conectividad
traceroute google.com           # Trazar ruta a un host
nslookup google.com             # Resolver DNS
netstat -tuln                   # Ver puertos abiertos y servicios
```
## 💻 Información del sistema

```bash
uname -a                        # Información del kernel y sistema
lscpu                            # Información detallada de CPU
free -h                          # Memoria usada y libre
df -h                            # Espacio en disco por partición
top                              # Procesos en ejecución en tiempo real
htop                             # Procesos en tiempo real con interfaz visual
lsblk                            # Discos y particiones
cat /proc/meminfo                 # Información detallada de memoria
sudo dmidecode                    # Información completa del hardware
```
## 📁 Gestión de archivos

```bash
ls -la                           # Listar archivos con detalles
cd [carpeta]                     # Cambiar directorio
cp [origen] [destino]            # Copiar archivos
mv [origen] [destino]            # Mover o renombrar archivos
rm [archivo]                     # Borrar archivos
mkdir [carpeta]                  # Crear nueva carpeta
rmdir [carpeta]                  # Eliminar carpeta vacía
chmod 755 [archivo/carpeta]      # Cambiar permisos
chown usuario:grupo [archivo]    # Cambiar propietario de archivo
```
## 🌐 Redes avanzadas
```bash
sudo ifconfig [interfaz] down/up  # Deshabilitar / habilitar interfaz
sudo ip link set [interfaz] up     # Activar interfaz
sudo ip route show                 # Mostrar rutas de red
sudo netplan apply                 # Aplicar configuración de red (Ubuntu)
```
## 🧩 Consejos adicionales

- Usa man [comando] para ver la documentación completa de cualquier comando.

- Ejecuta comandos que modifican el sistema como sudo con cuidado.

- Mantén este archivo como referencia rápida para soporte técnico Linux.
