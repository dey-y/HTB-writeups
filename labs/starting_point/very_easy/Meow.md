# HTB Starting Point — Meow

**Plataforma:** Hack The Box | Starting Point
**Dificultad:** Very Easy | **SO:** Linux

## Descripción

Máquina introductoria orientada a familiarizarse con el entorno de HTB, la conexión VPN y el uso de herramientas básicas de reconocimiento y acceso remoto.

## Conceptos aprendidos

- Configuración y establecimiento de túneles VPN con OpenVPN para acceder a entornos de laboratorio aislados
- Uso de terminal como interfaz principal de interacción
- Verificación de conectividad mediante ICMP (ping)
- Reconocimiento de puertos y servicios con Nmap
- Identificación del servicio Telnet (puerto 23/tcp) como vector de entrada
- Riesgos de credenciales débiles o inexistentes en servicios legacy

## Proceso técnico

1. Conexión al laboratorio mediante OpenVPN
2. Verificación de conectividad con `ping <IP>`
3. Escaneo de puertos con `nmap -sV <IP>` — detectado Telnet en puerto 23
4. Acceso al sistema vía `telnet <IP>` con usuario `root` sin contraseña
5. Enumeración del sistema de archivos y extracción de la flag

```bash
sudo openvpn --config archivo.ovpn
ping <IP>
nmap -sV <IP>
telnet <IP>
# login: root
# password: (vacío)
cat /root/flag.txt
```

## Herramientas utilizadas

`openvpn` · `ping` · `nmap` · `telnet`
