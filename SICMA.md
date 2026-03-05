<p align="center">
  <img width="300" src="https://github.com/user-attachments/assets/af01effb-5403-4ea5-914f-1153af2ebf86" alt="Logo SICMA" />
</p>

# SICMA Profesional

## Índice

1. Briefing  
2. Arquitectura del software  
3. Tecnologías a utilizar  
4. Red  
   - Diagrama de red   
5. Web    
   - Mockup   
6. Servicios  
   - DNS
   - DHCP
   - Apache
   - Firewall
   - Copias de seguridad
8. Conclusiones  
9. Bibliografía  

</details>

---

<details>
  <summary><strong> Briefing</strong></summary>

SICMA Profesional es una empresa de limpieza integral ubicada en Barcelona, que ofrece servicios para comunidades, oficinas, colegios y limpiezas especiales. Se enfoca en ofrecer calidad, confianza, detalle y soluciones adaptadas a las necesidades de cada cliente.

Teniendo en cuenta que la empresa familiar cuenta con un sitio web poco profesional me he propuesto crear un sitio web con un estilo más moderno, eficiente ....

El objetivo del proyecto es disponer de una plataforma web informativa que muestre los servicios, la experiencia de la empresa, ejemplos de trabajos realizados, comentarios de clientes y un apartado de contacto para solicitar presupuestos sin compromiso.

WEB actual:
https://cys-sicma.com/

**Que quiero mejorar de la web**
- Diseño
- Demasiado texto, resumir la información
- Eliminar el mapa
- Modificar la ubicación del contacto
- Logo blanco sobre fondo oscuro
- Scroll automatico
- Algunos botones no funcionan
- Imágenes más atractivas y fotos con explicación de la limpieza



</details>

---

<details>
  <summary><strong> Arquitectura del software</strong></summary>
  
Funcionalidades: 
- El login/registro de los usuarios
- Tipos de usuarios: clientes
- Administradores (yo)
- Permitir que los usuarios puedan comentar y pedir presupuesto


</details>

---

<details>
  <summary><strong> Tecnologías a utilizar</strong></summary>

#### Web 
- **Apache**
- **Xampp**
- **Wordpress**

**1. Instalación de Wordpress**

Descargué WordPress desde wordpress.org y dirigindome a Get Wrdpress, al terminar la descarga lo guardo en el disco C dentro de la carpeta de XAMPP, en htdocs, y descomprimi el archivo ZIP. Después habilité Apache y MySQL desde XAMPP; entré en phpMyAdmin, creé una base de datos llamada wordpress y un usuario llamado Pau, le asigné la contraseña y habilité todos los privilegios. A continuación cambié el nombre de la carpeta wordpress a sicma y, dentro de esa carpeta, edité el archivo wp-config.php, donde configuré el nombre de la base de datos como wordpress, el usuario como root, sin contraseña, y el servidor como localhost. Luego escribí localhost/sicma en el navegador y comenzó el proceso de instalación y configuración de WordPress: elegí el idioma español, asigné como título del sitio SICMA, configuré el usuario root, la contraseña y my correo electrónico. Tras pulsar en instalar WordPress, accedí con el nombre de usuario y la contraseña. A partir de aquí comienza el proceso de creación de la web, en el que, desde el escritorio, desactivé algunas opciones de pantalla para evitar distracciones y, posteriormente, me dirigí al apartado de Entradas, seleccioné Añadir entrada y añadí la información de la empresa. A partir de  aquí comienzo con la edición de la web.

**2. Servidor Apache**

Servidor Apache

1. Instalación y Configuración Inicial de Apache
Lo primero que hago es tomar el control como root para tener permisos totales. Actualizo los repositorios para asegurarme de que bajo las versiones más recientes y estables.
Entrar como root: su -
Comandos: apt update y apt install apache2 para instalarlo.

Gestionar el servicio:
- Iniciar y habilitar: systemctl start apache2 y systemctl enable apache2
- Verificar el estado: systemctl status apache2

Configuración de Red (Modo Puente): Cambiar el adaptador de la MV a Adaptador Puente.
- Identificar la nueva IP con el comando: ip a

2. Conexión Remota vía SSH 
Para evitar líos con el idioma del teclado en la MV y poder copiar/pegar comandos, conectamos el PC con la MV:
- Instalar SSH en la MV: apt install ssh

Conexión desde el CMD del PC:
- Abro el CMD del ordenador principal.
- Escribe: ssh usuario@ip_de_la_mv
A partir de aquí, puedo copiar los comandos y pegarlos directamente en la terminal.

3. Preparación del Directorio
Creao la carpeta del proyecto:
- Entar en: cd /var/www
- Crear la carpeta: mkdir sicma

Gestión de Permisos:
- Añadir mi usuario al grupo sudo: usermod -aG mi nombre
- Cambiar propietario a mi usuario: chown -R nombre /var/www/sicma
- Cambiar permisos a 755: chmod 755 sicma -R

4. Configuración del Virtual Host (sicma.conf)
Creao el archivo de configuración: sudo nano /etc/apache2/sites-available/sicma.conf
Pegar la configuración básica:

<p align="center"> <img width="1444" height="751" alt="image" src="https://github.com/user-attachments/assets/d337f450-6dc0-44a7-8985-fdb0455f3afc" /> </p>

- ServerAdmin webmaster@localhost
- ServerName your_domain
- ServerAlias www.your_domain
- DocumentRoot /var/www/your_domain

5. Activación del Sitio y Verificación
Habilitar y Deshabilitar sitios:
- Activar sicma: sudo a2ensite sicma.conf
- Desactivar el sitio por defecto: sudo a2dissite 000-default.conf

Validar y Reiniciar:
- Comprobar errores de sintaxis: sudo apache2ctl configtest
- Aplicar cambios: sudo systemctl reload apache2

Prueba Final:
Creao un archivo de prueba: nano /var/www/sicma/index.html
Acceder desde el navegador del PC usando la IP de la MV: http://ip_de_la_mv

6. Instalación de PHP
- Instalo PHP y el módulo que lo conecta con Apache: sudo apt install php libapache2-mod-php.

El problema de la prioridad
Aquí es donde noto que, si tengo un index.html y un index.php juntos, el servidor siempre me muestra el HTML primero. Para cambiar esto, edito el archivo de prioridades: sudo nano /etc/apache2/mods-enabled/dir.conf.
Modifico el orden para que index.php esté al principio de la lista. Guardo y reinicio con systemctl reload apache2. Ahora, mi servidor buscará primero la lógica de programación (PHP) antes que el contenido estático (HTML).

7. Probar el procesamiento de PHP en su servidor web
Ahora que el servidor es capaz de leer PHP, verifico que todo funcione dentro de mi carpeta de proyecto (sicma).

Creación del archivo de prueba
Estando como root.
- Ejecuto: nano /var/www/sicma/index.php
- Escribo el siguiente código:

<p palign="center"> <img width="1208" height="104" alt="image" src="https://github.com/user-attachments/assets/38e1c9ef-c293-4a0e-842c-5672e9128fac" /> </p>


- Guardo y cierro. Ahora abro mi navegador en el PC y accedo a: http://ip_de_la_mv. Si veo la tabla informativa de PHP, ¡el servidor está vivo!

El conflicto de prioridad: index.html vs index.php. Aquí noto un detalle: si en mi carpeta sicma tengo un index.html y un index.php, al entrar a la ip dela mv siempre me muestra el HTML. Esto pasa porque Apache, por defecto, le da prioridad a los archivos estáticos.

- Para que mi servidor prefiera ejecutar PHP antes que mostrar HTML, modifico la configuración del módulo dir:
- Abro el archivo de configuración: sudo nano /etc/apache2/mods-enabled/dir.conf
- Muevo index.php al principio de la lista, justo después de DirectoryIndex:

<p palign="center"> <img width="1210" height="56" alt="image" src="https://github.com/user-attachments/assets/b8f11843-a0e5-42da-8298-b1f8b8d993c6" /> </p>

- Guardo los cambios y reinicio Apache para establecer los cambios: sudo systemctl reload apache2
  

#### Base de Datos
- **Xampp**
- **MySQL**
- **Workbench**

**1. Creación de la db**

Para la creación la de la base de datos, habilité MySQL desde XAMPP; entré en Workbench y me dirigí al símbolo mas en MySQL connections, le llame por el nimbre de la empresa **SICMA** y puse el puerto que me habilitado el XAMPP **3307**. Ahora creo la base de datos atreves de comandos.
<p align="center"> <img width="513" height="796" alt="image" src="https://github.com/user-attachments/assets/0a3f6962-6357-4bd5-ac69-9a5d65bed57f" /> </p>

**2. Creación del diagrama de la db**

Para la creacio del diagrama, se creó un nuevo modelo desde la opción File; New Model, añadiendo posteriormente un diagrama EER. A continuación, se fueron creando las distintas tablas del sistema utilizando la herramienta de añadir tabla, definiendo para cada una de ellas sus campos, tipos de datos y claves primarias.

El modelo se organiza en **tres niveles** de información. En el nivel **principal** se encuentra la tabla Servicios, que representa los servicios ofrecidos y constituye la base del sistema. En el nivel **secundario** está la tabla Usuario, que almacena los datos de las personas registradas y sirve como punto de conexión para otras entidades relacionadas. A partir de estas tablas derivan las entidades de interacción, como Comentario y Presupuesto, que también forman parte del nivel secundario y permiten registrar valoraciones, mensajes y solicitudes de presupuesto realizadas por los usuarios. Finalmente, la **función** que corresponde a la tabla User_has_Servicios cumple una función operativa, ya que actúa como puente entre Usuario y Servicios, estableciendo una relación de muchos a muchos y registrando los servicios asociados a cada usuario. Esta estructura organiza los datos de manera clara, separando lo esencial de lo complementario y permitiendo un flujo funcional entre las entidades.
<p align="center"> <img width="858" height="619" alt="image" src="https://github.com/user-attachments/assets/0dd771dc-1fd7-4b2e-9e92-11c8d1c60235" /> </p>

  
#### DNS
- **Pi-hole**

A tener en cuenta:
https://punkymo.gitbook.io/miwiki/virtualizacion/contenedores/pi-hole/instalando-pi-hole-en-debian

1. No uso debian, sino Ubuntu Server.
2. Utilizó netplan.
3. No puedo usar RedNat, sin dos adaptadores de red: Puente y Red Interna.

Adaptador 1 (enp0s3): Puente - DHCP

Adaptador 2 (enp0s8): Red Interna - IP estática

Que he hecho:
Primero poner el adaptador 1 en adaptador puente y adaptador 2 en red interna. Despues configurar el netplan dentro de la maquina virtual utilizando el comando, **sudo nano /etc/netplan/00-installer-config.yaml**

poner:
<p align="center"> <img width="574" height="312" alt="image" src="https://github.com/user-attachments/assets/295d6eab-ce8e-45ff-a9d8-558921a8e5ae" /> </p>

- Ctrl + O --> guardar
- Ctrl + X --> salir

Despues utilizo los comando, **sudo netplan apply** y **sudo netplan try** para aplicar la configuración de netplan, acontinuacion **ip a** para comprobar si me da una ip fija. Despues hacer ping con google para comprobar que tengo internet, **ping google.com**.

Por ultimo instalar y configurar Pi-hole, con el comando **curl -sSL https://install.pi-hole.net | bash**
- seleccionar la interfaz de red (enp0s8)
- seleccionar el servidor DNS google
- dejar activado listas de bloqueo
- Web Admin Interface --> si
- Web Server (lighttpd) --> si


Incidencias:
- El comando, sudo nano /etc/netplan/00-installer-config.yaml lo escribí y configure mal. Y después lo puse otra vez pero escribiendo y configurandolo bien, entonces tenia 2 netplans, y la mv cojia la que estaba mal, entonces tuve que elimine la la que estava mal.
  
#### Backup
- **Truenas**
- **Rsync**

#### Firewall
- **pf sense**

</details>

---

<details>
  <summary><strong>Red</strong></summary>

#### Diagrama de red  
<p align="center"> <img width="1289" height="469" alt="image" src="https://github.com/user-attachments/assets/582cea4e-5878-483a-b0f0-ec80374ee58a" /> </p>




</details>

---

<details>
  <summary><strong> Web</strong></summary>
  

#### Mockup  
**Sección: Inicio**

Navegabilidad: El usuario entra al sitio y ve un resumen de los servicios principales, información destacada y un botón de acción que lo lleva a la sección de Presupuesto.

<p align="center"> <img width="300" src="https://github.com/user-attachments/assets/19ff836a-1595-4334-9085-f518a3a57552" /> <img width="300" src="https://github.com/user-attachments/assets/cb2d4512-74ba-4b82-b9f4-a5199eef1e22" /> </p>


**Sección: Servicios**

Navegabilidad: Desde esta sección, el usuario puede ver todos los servicios disponibles y un boton de acción para acceder directamente al Contacto.
<p align="center"> <img width="300" src="https://github.com/user-attachments/assets/076f0519-086d-4a13-9867-4e7a681878f9" /> <img width="300" src="https://github.com/user-attachments/assets/e7b8371f-766b-4acc-82c1-b68a622e1bbd" /> <img width="300" src="https://github.com/user-attachments/assets/bc41a29e-b3aa-4006-bf8e-3c9fc400af1a" /> <p align="center"> <img width="300" src="https://github.com/user-attachments/assets/2764f7af-adef-4169-aa4b-4a68dc19f4b7" /> <img width="300" src="https://github.com/user-attachments/assets/d23c5fe4-1584-4761-8af3-8d803f9c1f2e" /> </p>


**Sección: Galería**

Navegabilidad: Permite al usuario explorar trabajos anteriores. Cada imagen puede ampliarse.

<p align="center"> <img width="300" src="https://github.com/user-attachments/assets/235b4bd8-1020-423e-a1ae-35c06bcb710c" /> <img width="300" src="https://github.com/user-attachments/assets/04edabc9-5ccb-4fc2-8d7e-6a367be8133e" /> </p>



**Sección: Testimonio**

Navegabilidad: Muestra los comentarios de clientes guardados. Desde aquí, el usuario puede poner los comentario que quiera del servicio realizado.

<p align="center"> <img width="300" src="https://github.com/user-attachments/assets/dc345740-9641-4c26-81a5-02ea6fd91bf0" /> </p>


**Sección: Contacto**

Navegabilidad: Formulario de contacto. Desde aquí, el usuario puede solicitar un presupuesto.

<p align="center"> <img width="300" src="https://github.com/user-attachments/assets/16679530-33bc-4b8a-aedb-b6f6257a1241" /> </p>


</details>

---

<details>
  <summary><strong> Servicios</strong></summary>

  
**Apache**

1. ¿Qué función cumple exactamente este servicio dentro de la red?

- Aloja y sirve el sitio web de SICMA Profesional. Resuelve el problema de la presencia digital, permitiendo que los clientes accedan a la información y soliciten presupuestos desde cualquier navegador. Da servicio a los clientes externos (público) y administradores.

2. ¿En qué equipo se instala y qué requisitos necesita?

Incluye:

- SO: Debian.

- IP: IP estática (192.168.135.59).

- Recursos: 2 CPU, 2GB RAM, 20GB Disco.

3. ¿Qué parámetros básicos debo configurar?

- Puertos: 80 (HTTP), 443 (HTTPS) y 22 (TCP).

- Directorio: /var/www/sicma.

- Archivo principal: /etc/apache2/sites-available/sicma.conf.

4. ¿Cómo verifico que funciona correctamente?

- systemctl status apache2

- Acceso desde el PC host escribiendo la IP de la MV en el navegador.

- Logs en /var/log/apache2/error.log.

5. ¿Qué aspectos de seguridad debo revisar?

- Permisos 755: permite que el servidor web navegue por el directorio pero solo el administrador pueda crear o borrar carpetas..

- Desactivar el listado de directorios (Options -Indexes).

- UFW: sudo ufw allow 'Apache Full'.

**DNS**

1. ¿Qué función cumple exactamente este servicio dentro de la red?

- Traducir nombres de dominio en direcciones IP. En mi red, resuelve el problema de la navegación lenta y la publicidad, además de permitir crear nombres locales para tus servidores.

2. ¿En qué equipo se instala y qué requisitos necesita?

Incluye:

- SO: Ubuntu Server.

- IP: Estática (192.168.1.134).

- Recursos: 10096MB RAM, 15GB Disco.

3. ¿Qué parámetros básicos debo configurar?

- Puertos: 53 (DNS), 80 (Panel Web).

- Configuración: Local DNS Records para apuntar sicma.com a mi IP local.

- DNS de origen: Google (8.8.8.8).

4. ¿Cómo verifico que funciona correctamente?

- pihole status en la terminal.

- Desde un cliente: nslookup sicma.com (debe devolver la IP de mi servidor).

- Acceso al dashboard: http://<IP_PIHOLE>/admin.

5. ¿Qué aspectos de seguridad debo revisar?

- Cambiar contraseña del panel (pihole -a -p).

- No exponer el puerto 53 a internet (solo red interna).

**DHCP**

1. ¿Qué función cumple exactamente este servicio dentro de la red?

- Asigna automáticamente direcciones IP a los dispositivos de la red de SICMA. Resuelve el problema de tener que configurar manualmente cada ordenador o móvil que se conecte, evitando conflictos de IPs duplicadas.

2. ¿En qué equipo se instala y qué requisitos necesita?

- SO: Ubuntu Server (donde reside Pi-hole).

- IP: La IP estática de mi servidor Pi-hole (192.168.1.134).

- Dependencias: El protocolo DHCP utiliza internamente dnsmasq (que ya viene dentro de Pi-hole).

3. ¿Qué parámetros básicos debo configurar?

- Puertos: 67 (servidor) y 68 (cliente) UDP.

- Rango DHCP: Por ejemplo, de 192.168.1.50 a 192.168.1.150.

- Gateway: La IP de mi pfSense.

4. ¿Cómo verifico que funciona correctamente?

- Prueba: Conectar un cliente nuevo y ejecutar ipconfig (Windows) o ip a (Linux) para ver si recibe IP del rango.

- Panel: Revisar la sección "DHCP leases" en la interfaz web de Pi-hole.

5. ¿Qué aspectos de seguridad debo revisar?

- Static Leases: Reservar IPs fijas por dirección MAC para los equipos críticos (como el servidor Apache).

**Firewall**

1. ¿Qué función cumple exactamente este servicio dentro de la red?

- Actúa como la primera línea de defensa. Filtra todo el tráfico que entra y sale de la empresa SICMA. Resuelve el problema de accesos no autorizados y ataques desde internet (WAN).

2. ¿En qué equipo se instala y qué requisitos necesita?

- SO: pfSense (basado en FreeBSD).

- IP: Suele tener dos: la WAN (pública o del router) y la LAN (puerta de enlace, ej. 192.168.1.1).

- Recursos: 2 CPUs, 2GB RAM, 2 tarjetas de red (mínimo).

3. ¿Qué parámetros básicos debo configurar?

- Reglas de Firewall: Definir qué puertos están abiertos (80, 443 para la web).

- NAT / Port Forwarding: Redirigir el tráfico que llega a la IP pública hacia la IP interna de mi servidor Apache.

- Interfaces: WAN (entrada de internet) y LAN (red local de la oficina).

4. ¿Cómo verifico que funciona correctamente?

- Comando: En el menú de pfSense, opción 8 (Shell) y usar pfctl -s rules para ver las reglas activas.

- Prueba: Intentar acceder a un servicio bloqueado y verificar que la conexión es rechazada.

- Logs: Revisar en la web: Status > System Logs > Firewall.

5. ¿Qué aspectos de seguridad debo revisar?

- Regla "Deny All" por defecto: Bloquear todo lo que no esté explícitamente permitido.

- Anti-Spoofing: Evitar que alguien finja una IP interna desde fuera.

- Acceso Remoto: Solo permitir el acceso a la interfaz de administración (WebGUI) desde la LAN, nunca desde la WAN.

**Copias de seguridad** 

1. ¿Qué función cumple exactamente este servicio dentro de la red?

- TrueNAS: Gestiona el almacenamiento físico mediante el sistema de archivos ZFS, garantizando la integridad de los datos (evita que los archivos se corrompan).

- Rsync: Realiza copias incrementales. Su función es sincronizar los archivos de la web y la base de datos desde el servidor Apache hacia el TrueNAS, transfiriendo solo los bloques de datos que han sido modificados

2. ¿En qué equipo se instala y qué requisitos necesita?

- SO: TrueNAS.

- Protocolo: Rsync / SSH.

- Recursos: 3099MB RAM, 3 Discos 16 GB.

3. ¿Qué parámetros básicos debo configurar?

- Puertos: SSH y Rsync.

- Tarea: Programar una tarea diaria.

4. ¿Cómo verifico que funciona correctamente?

- Revisar el historial de tareas en el panel de TrueNAS.

- Verificar que los archivos están físicamente en el pool de discos de respaldo.

5. ¿Qué aspectos de seguridad debo revisar?

- Uso de llaves SSH en lugar de contraseñas para la automatización.

</details>

---

<details>
  <summary><strong> Conclusiones</strong></summary>

La web permite aumentar la visibilidad digital de SICMA Profesional, mejorar la comunicación con los clientes y facilitar la solicitud de servicios.

</details>

---

<details>
  <summary><strong> Bibliografía</strong></summary>


</details>
