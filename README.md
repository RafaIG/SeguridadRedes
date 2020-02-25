

# Ejercicio para clase Tema 3

### Configuración básica de R1:
- Nombre
<br/>`Router(config)#hostname ejercicio3`

- Contraseña de consola
<br/>`ejercicio3(config)#line console 0`
<br/>`ejercicio3(config-line)#password password`
<br/>`ejercicio3(config-line)#login`

- Contraseña de enable
<br/>`ejercicio3(config)#enable secret password`

- Banner motd (message of the day)
<br/>`ejercicio3(config)#banner motd x Hoola, buenos das campen! x`

- Un usuario admin con permisos de administración
<br/>`ejercicio3(config)#username admin privilege 15`

- Un usuario user con permisos básicos
<br/>`ejercicio3(config)#username user privilege 1`
<br/>`ejercicio3(config)#line console 0`
<br/>`ejercicio3(config-line)# login local`

- Acceso por SSH
<br/>`Router(config)#hostname practica3`
<br/>`practica3(config)#ip domain-name practica3dominio`
<br/>`practica3(config)# crypto key generate rsa general-keys` Seleccionar al menos 768
<br/>`practica3(config)#ip ssh version 2`
<br/>`practica3(config)# line vty 0 15`
<br/>`practica3(config-line)# transport input ssh`
<br/>`practica3(config-line)# login local`
<br/>`practica3(config-line)# exit`
<br/>`practica3(config)#username admin password password`

- Configuración de seguridad frente a intentos de acceso por fuerza bruta (delay, block-for, reinentos de SSH)
<br/>`practica3(config)#ip ssh authentication-reties 3`
<br/>`practica3(config)# ip ssh time-out 30`

### Configuración de red en los switches:
- Configuración de red de los switches sw1, sw2, sw3 y sw5, , con una IP libre del rango en el que se encuentran sus equipos.
- Configuración de red del switch sw4 con una IP de la vlan 3.

### NTP de todos los routers frente al servidor Serv_SYSLOG con contraseña miercoles

### Syslog
- Los equipos de B (switches y routers) registrarán mensajes de syslog en Serv_SYSLOG, con sello de tiempo, usando siempre sus direcciones IP internas (en caso de los routers que tienen varias, y para R2, la de la Zona 2).
- Los equipos de la Zona A registrarán en Serv_SYSLOG_A, que está en dirección privada pero tiene redirigido el puerto 514 UDP del router hacia él.

### AAA
- Autenticación de R2 y R3 sobre el servidor Serv_SYSLOG que hace de servidor AAA con acceso TACACS+. Creación de accesos autenticados en dicho servidor, con una password por cliente.
- Creación de usuarios en dicho servidor
- Autenticación sobre dicho servidor y, en caso de fallar, sobre la base de datos local con un usuario admin/1234 de backup.
