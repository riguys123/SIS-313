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

<img width="1264" height="655" alt="image" src="https://github.com/user-attachments/assets/807a8b24-421a-486a-a88a-225998a79584" />

<img width="1042" height="466" alt="image" src="https://github.com/user-attachments/assets/586c91c3-0995-4f5c-818c-38c7d106ad4b" />


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

descargamos windowsXP "https://drive.google.com/file/d/15WkIfyDBozsMHGsf_QsSJFS_0E9wdmAV/view"

instalamos y colocamos la ISO del paquete que descargamos. 

cambiamos la configuracion a red interna. 

## En la maquina con WindowsXP

** aqui entraremos a la interfaz web de PfSense con la ip estatica que acabamos de asignar "https://10.10.1.254"

<img width="725" height="483" alt="image" src="https://github.com/user-attachments/assets/3601152d-787d-4771-ae7c-29382e0bea78" /> 

press enter

<img width="725" height="481" alt="image" src="https://github.com/user-attachments/assets/fb02e800-e8f1-448f-90da-89e868ea7f5a" />

luego en esta imagen nos aparecera los contratos de windows ahi presionamos f8

<img width="715" height="482" alt="image" src="https://github.com/user-attachments/assets/1bd3d41b-202e-455b-9d5d-26effd94471a" />

aqui nos aparecera la particion de la MV aqui presionamos enter 

<img width="719" height="490" alt="image" src="https://github.com/user-attachments/assets/7603df59-2b1c-47cc-9f46-87b85e457fdd" />

aqui seleccionamos "formatea la particion utilizando el sistema de archivos NTFS(rapido)"

luego comienza la particion. 

<img width="637" height="569" alt="image" src="https://github.com/user-attachments/assets/e13dfd74-06a8-4fa4-a7db-718dfd30c404" />

al acabar de instalar nos saldra la ventana de configuracion regionales y de idioma 

<img width="640" height="578" alt="image" src="https://github.com/user-attachments/assets/715296da-5c91-4ba4-aaca-ca1521c08151" />

ponemos el nombre en la casilla de organizacion, es opcional



