# TRABAJO PORTAL CAUTIVO SIS-313

## INTEGRANTES G-06
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

<img width="726" height="488" alt="image" src="https://github.com/user-attachments/assets/37a88b1b-eb3d-4d4b-b9d8-7d91634d0b45" />



press 1 
(y/n): n enter
(em0 em1 or a): em0 enter 
(em0 em1 or a): em1 enter 

<img width="721" height="498" alt="image" src="https://github.com/user-attachments/assets/80979c09-7b3a-4757-8bad-eaec6f427373" />


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

<img width="645" height="575" alt="image" src="https://github.com/user-attachments/assets/914aee5c-77a4-4a11-a351-4ecab1a3de0b" />

ponemos la clave del producto de windows xp "M8DPF-XT324-YBKK9-3VF8C-M2X78" 

<img width="640" height="563" alt="image" src="https://github.com/user-attachments/assets/6a18aca6-272d-4b4e-b902-e09a8b422ecf" />

presionamos siguiente sin colocar la contraseña

<img width="641" height="570" alt="image" src="https://github.com/user-attachments/assets/ac9d4691-e65e-4cdb-a89c-98c15357b6ce" />

configuramos la hora y region

<img width="638" height="566" alt="image" src="https://github.com/user-attachments/assets/178d5bf5-a822-4ca9-a7da-44832a49b5fa" />

al configurar la red la dejamos en tipica 

<img width="643" height="576" alt="image" src="https://github.com/user-attachments/assets/bf0c3611-3869-4364-b26b-24448a165d61" />

press siguiente 

<img width="799" height="684" alt="image" src="https://github.com/user-attachments/assets/0c0962da-9c09-4665-8377-8404a54959a2" />

presionamos siguiente

<img width="795" height="689" alt="image" src="https://github.com/user-attachments/assets/cfe3cb7c-bf15-49ac-ad83-9df917d4b760" />

presionamos siguiente

<img width="795" height="689" alt="image" src="https://github.com/user-attachments/assets/5791e7bc-4358-4b85-b518-abdba89a479b" />

seleccionamos la opcion de "no en este momento"

<img width="804" height="699" alt="image" src="https://github.com/user-attachments/assets/b77615b3-0b1b-4def-8783-9d4eaca367e3" />

press omitir

<img width="806" height="695" alt="image" src="https://github.com/user-attachments/assets/b3baa40b-8a0b-4ac1-8e37-accdcca8c5be" />

seleccionamos la opcion de "no en este momento"

<img width="805" height="687" alt="image" src="https://github.com/user-attachments/assets/6dc6d5f8-9a7b-4bc6-9205-400b3e1abadb" />

colocamos un nombre 

<img width="803" height="691" alt="image" src="https://github.com/user-attachments/assets/64688347-9214-42f9-9587-f2a3ad529560" />

y finalizamos

<img width="805" height="691" alt="image" src="https://github.com/user-attachments/assets/99ea63ed-b83d-482c-86bd-0693a688e833" />

y ya estaria intalado windowsXP

##Configuraciones en PfSense

<img width="637" height="574" alt="image" src="https://github.com/user-attachments/assets/15f4bc48-df0e-4b45-a839-ade4dce33e04" />

entramos a inicio a mi pc y vemos si nuestra maquina esta conectada con la ip asignada

<img width="639" height="567" alt="image" src="https://github.com/user-attachments/assets/cc94156b-ed86-4a1d-9806-6090fdf24e60" />

desactivamos y activamos

<img width="644" height="581" alt="image" src="https://github.com/user-attachments/assets/9c8540ac-919a-48bb-b7d4-95841e3cf453" />

aqui verificamos la ip

<img width="643" height="570" alt="image" src="https://github.com/user-attachments/assets/b2b38ac9-f3c8-4be4-896c-9b822bfa44f2" />

ponemos la ip para ingresar al pfsense

<img width="654" height="567" alt="image" src="https://github.com/user-attachments/assets/536769f7-4704-4728-b24b-8c096fdb3497" />

aqui nos logueamos 

<img width="844" height="578" alt="image" src="https://github.com/user-attachments/assets/67a655fa-be92-4ce4-be4d-20e5017ec7f7" />


ingresamos al pfsense

<img width="857" height="571" alt="image" src="https://github.com/user-attachments/assets/10a22157-0b75-4f0f-9a9d-39d936cb5c9c" />

dentro del pfsense entramos a system a user manger para crear los usuarios para portal cautivo

<img width="1600" height="789" alt="image" src="https://github.com/user-attachments/assets/512cb6f0-6934-431f-9151-fd04eef10fec" />

aqui creamos los usuarios para el portal cautivo

<img width="858" height="574" alt="image" src="https://github.com/user-attachments/assets/ec3ca4e6-1962-47c2-b42b-22d73c7663e1" />

aqui creamos grupos 

<img width="1232" height="514" alt="image" src="https://github.com/user-attachments/assets/c54af6fb-045d-4837-b47a-6d85668ee53e" />

aqui entramos para luego configurar el ancho de banda

<img width="1203" height="410" alt="image" src="https://github.com/user-attachments/assets/a4c10b26-f9f7-435b-9fa4-c5051c5b0319" />

configuramos el ancho de banda por ususario

<img width="1227" height="883" alt="image" src="https://github.com/user-attachments/assets/15f78495-4dcb-422a-afd7-f0a77d3a0e26" />

entramos al voucher para autenticar a los clientes 

<img width="1235" height="875" alt="image" src="https://github.com/user-attachments/assets/01368214-56fb-4bfb-8a07-857bffbd496d" />

En esta parte configuramos la duracion del internet que podra usar el cliente y el numero de vouchers a generar 

<img width="1172" height="165" alt="image" src="https://github.com/user-attachments/assets/19ecc8a6-4b8f-4e79-bb85-f1b1b89243bc" />

aqui descargamos el archivo de vouchers 

<img width="827" height="475" alt="image" src="https://github.com/user-attachments/assets/f2605d9c-6b07-412b-a601-4f92c1a5415d" />

este es el archivo que se genero 

## Conclusion del proyecto 

La práctica técnica mostrada configura con éxito una solución de control de acceso a la red, utilizando el sistema PfSense para implementar un Portal Cautivo. Esto permite al administrador gestionar y autenticar a los usuarios de la red mediante la emisión de vouchers, asegurando que solo los usuarios autorizados tengan acceso a Internet de manera temporal y controlada.













