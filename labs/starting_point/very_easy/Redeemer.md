# HTB Starting Point — Redeemer

**Plataforma:** Hack The Box | Starting Point
**Dificultad:** Very Easy | **SO:** Linux

## Descripción

Máquina orientada a la comprensión de Redis, una base de datos en memoria ampliamente utilizada, y a la explotación de instancias mal configuradas que permiten acceso sin autenticación.

## Conceptos aprendidos

- Funcionamiento de **Redis** como base de datos en memoria (In-memory Database)
- Escaneo de puertos no convencionales con `nmap -p-` para descubrir servicios fuera del rango por defecto
- Uso de `redis-cli` para interactuar con un servidor Redis sin autenticación
- Enumeración de bases de datos y extracción de claves con comandos básicos de Redis
- Riesgos de exponer instancias Redis sin autenticación en entornos de red

## Proceso técnico

1. Conexión al laboratorio mediante OpenVPN
2. Verificación de conectividad con `ping <IP>`
3. Escaneo completo de puertos con `nmap -sV -p- <IP>` — detectado Redis 5.0.7 en puerto 6379
4. Conexión al servidor Redis con `redis-cli -h <IP>`
5. Obtención de información del servidor con `info`
6. Selección de la base de datos con índice 0 con `select 0`
7. Listado de todas las keys con `keys *` — encontradas 4 keys
8. Extracción de la flag con `get <key>`

```bash
sudo openvpn --config archivo.ovpn
ping <IP>
nmap -sV -p- <IP>
redis-cli -h <IP>
# dentro de redis-cli:
info
select 0
keys *
get <nombre_de_la_key>
```

## Herramientas utilizadas

`openvpn` · `ping` · `nmap` · `redis-cli`
