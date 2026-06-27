# HTB Starting Point — Fawn

**Plataforma:** Hack The Box | Starting Point
**Dificultad:** Very Easy | **SO:** Linux

## Descripción

Máquina orientada a la comprensión del protocolo FTP, su funcionamiento, vulnerabilidades inherentes y métodos de acceso anónimo a servidores mal configurados.

## Conceptos aprendidos

- Funcionamiento del protocolo FTP (File Transfer Protocol) en el puerto 21
- Diferencias entre FTP (sin cifrado) y SFTP (cifrado, extensión de SSH)
- Uso del acceso anónimo en servidores FTP como vector de entrada habitual
- Navegación y descarga de archivos dentro de una sesión FTP
- Identificación de versiones de software expuestas (vsftpd 3.0.3) como punto de reconocimiento

## Proceso técnico

1. Conexión al laboratorio mediante OpenVPN
2. Verificación de conectividad con `ping <IP>`
3. Escaneo de puertos con `nmap -sV <IP>` — detectado FTP (vsftpd 3.0.3) en puerto 21, SO Unix
4. Conexión al servidor con `ftp <IP>` usando usuario `anonymous` sin contraseña
5. Listado de archivos con `ls` y descarga de la flag con `get flag.txt`
6. Lectura de la flag con `cat flag.txt`

```bash
sudo openvpn --config archivo.ovpn
ping <IP>
nmap -sV <IP>
ftp <IP>
# Name: anonymous
# Password: (vacío)
ls
get flag.txt
exit
cat flag.txt
```

## Herramientas utilizadas

`openvpn` · `ping` · `nmap` · `ftp`
