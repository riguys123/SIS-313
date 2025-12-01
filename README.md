# TRABAJO PORTAL CAUTIVO SIS-313

## INTEGRANTES
- TORRES BALCERA RODRIGO
- PEDRAZA VALVERDE JOSE MARIA
- JULIAN JOAN ALEXANDER
- SANCHEZ GALARZA MARCO ANTONIO

## OBJETIVO DEL PROYECTO
🎯 Objetivo de un Portal Cautivo

El objetivo principal de un portal cautivo es controlar y gestionar el acceso a una red, generalmente Wi-Fi, permitiendo que los usuarios se autentiquen o acepten ciertas condiciones antes de navegar en Internet.

Objetivos Especificos:

-Implementar un portal cautivo utilizando pfSense para gestionar y controlar el acceso a la red. 

-Configurar métodos de autenticación soportados por pfSense (Local, RADIUS, vouchers, etc.). 

-Redirigir automáticamente a los usuarios a la página de inicio de sesión del portal cautivo.

-Registrar actividad y conexiones mediante los logs internos de pfSense.

-Aplicar políticas de ancho de banda, tiempo de conexión y límites por usuario usando las funciones de Traffic Shaper.

-Personalizar el portal cautivo con plantillas HTML integradas en pfSense.

-Monitorear y administrar sesiones activas desde la interfaz de pfSense.

## Preparación del Entorno Virtual

Para la implementación del portal cautivo se configuró un entorno virtual compuesto por una maquina en la que haremos la configuracion de pfsense y otra maquina de cualquier sistema para poder acceder a la interfaz grafica de pfsense. 

De este enlace descargar pfsense  "https://digistorage.net/73kuhrc4" 

## En la maquina con pfsense.- 

hacemos la configuracion de la maquina por consola para asignar las ip a las interfaces. 

una vez en la interfaz nos aparecera un menu con varias opciones las unicas que usaremos seran la 1 y la 2 

press 1 
(y/n): n enter
(em0 em1 or a): em0 enter 
(em0 em1 or a): em1 enter 
[Y/N]: y enter
usaremos em0 para la WAN y em1 para la LAN asi ya estarian asignadas 

ahora asignaremos las respectivas ips en la WAN usaremos DHCP para que automaticamente el ISP o router externo nos la asigne.

en la LAN ocuparemos una estatica ya que esta nos servira para los clientes y repartir direcciones 

ahora en el menu nos vamos a la opcion 2

1 enter 

y enter

n enter 

enter

n enter

enter para continuar 

ya se asigno una ip automaticamente, ahora haremos con la LAN y aqui si le asignaremos una ip 

de nuevo presionamos la opcion 2 

2 enter

(ip que tendra la maquina) ejm 10.10.1.254

24 enter

enter

y enter ->activamos nuestro servicio dhcp

10.10.1.40 -> start rango

10.10.1.50 -> end rango

n enter 

enter para continuar

## Ahora nos vamos a la maquina virtual de windows XP
## En la maquina con WindowsXP

** aqui entraremos a la interfaz web de PfSense con la ip estatica que acabamos de asignar "https://10.10.1.254"




