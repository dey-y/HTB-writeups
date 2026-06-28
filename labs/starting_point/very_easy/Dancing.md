# HTB Starting Point — Dancing

**Plataforma:** Hack The Box | Starting Point
**Dificultad:** Very Easy | **SO:** Windows

## Descripción

Máquina orientada a la comprensión del protocolo SMB, su funcionamiento en entornos Windows y la explotación de shares mal configurados con acceso anónimo.

## Conceptos aprendidos

- Funcionamiento del protocolo SMB (Server Message Block) en el puerto 445
- Enumeración de shares SMB expuestos en un sistema Windows
- Acceso anónimo a shares sin credenciales como vector de entrada habitual
- Navegación por el sistema de archivos remoto y descarga de archivos dentro de una sesión SMB
- Identificación del servicio `microsoft-ds` como indicador de SMB activo
- Uso del flag `-Pn` en nmap para evitar el filtrado ICMP en máquinas Windows

## Proceso técnico

1. Conexión al laboratorio mediante OpenVPN
2. Verificación de conectividad con `ping <IP>`
3. Escaneo de puertos con `nmap -sV -Pn <IP>` — detectado SMB en puerto 445
4. Enumeración de shares con `smbclient -L <IP> -N -p 445` — identificados 4 shares: `ADMIN$`, `C$`, `IPC$` y `WorkShares`
5. Acceso al share **WorkShares** sin contraseña
6. Navegación por carpetas de usuarios (`Amy.J`, `James.P`) y descarga de la flag

```bash
sudo openvpn --config archivo.ovpn
ping <IP>
nmap -sV -Pn <IP>
smbclient -L <IP> -N -p 445
smbclient //<IP>/WorkShares -N -p 445
# dentro del shell SMB:
ls
cd James.P
get flag.txt
# salir del shell SMB:
exit
cat flag.txt
```

## Herramientas utilizadas

`openvpn` · `ping` · `nmap` · `smbclient`
