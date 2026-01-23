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
- Administradores (yo, mi madre)
- Permitir que los usuarios puedan comentar y pedir presupuesto


</details>

---

<details>
  <summary><strong> Tecnologías a utilizar</strong></summary>

#### Web 
- **Apache**
- **Xampp**
- **Wordpress**

Descargué WordPress desde wordpress.org y dirigindome a Get Wrdpress, lo copié en el disco C dentro de la carpeta de XAMPP, en htdocs, y descomprimi el archivo ZIP. Después habilité Apache y MySQL desde XAMPP; entré en phpMyAdmin, creé una base de datos llamada wordpress y un usuario llamado Pau, le asigné la contraseña slCKG/Ry@o.7* y habilité todos los privilegios. A continuación cambié el nombre de la carpeta wordpress a sicma y, dentro de esa carpeta, edité el archivo wp-config.php, donde configuré el nombre de la base de datos como wordpress, el usuario como root, sin contraseña, y el servidor como localhost. Luego escribí localhost/sicma en el navegador y comenzó el proceso de instalación y configuración de WordPress: elegí el idioma español, asigné como título del sitio SICMA, configuré el usuario root, la contraseña u3KZ8z4UIWq9jQtA^N y my correo electrónico (pauferrer2007.pfc@gmail.com). Tras pulsar en instalar WordPress, accedí con el nombre de usuario y la contraseña. A partir de aquí comienza el proceso de creación de la web, en el que, desde el escritorio, desactivé algunas opciones de pantalla para evitar distracciones y, posteriormente, me dirigí al apartado de Entradas, seleccioné Añadir entrada y añadí la información de la empresa. A partir de  aquí comienzo con la edición de la web.
  

#### Base de Datos
- **Xampp**
- **MySQL**
- **Workbench**

Para la creación la de la base de datos, habilité MySQL desde XAMPP; entré en Workbench y me dirigí al símbolo mas en conaciones, le llame SICMA y puse el puerto que me habilitado el XAMPP (3307). Ahora creo la base de datos atreves de comandos.
<p align="center"> <img width="513" height="796" alt="image" src="https://github.com/user-attachments/assets/0a3f6962-6357-4bd5-ac69-9a5d65bed57f" /> </p>

Para la creacio del diagrama, se creó un nuevo modelo desde la opción File; New Model, añadiendo posteriormente un diagrama EER. A continuación, se fueron creando las distintas tablas del sistema utilizando la herramienta de añadir tabla, definiendo para cada una de ellas sus campos, tipos de datos y claves primarias.

El modelo se organiza en tres niveles de información. En el nivel principal se encuentra la tabla Servicios, que representa los servicios ofrecidos y constituye la base del sistema. En el nivel secundario está la tabla Usuario, que almacena los datos de las personas registradas y sirve como punto de conexión para otras entidades relacionadas. A partir de estas tablas derivan las entidades de interacción, como Comentario y Presupuesto, que también forman parte del nivel secundario y permiten registrar valoraciones, mensajes y solicitudes de presupuesto realizadas por los usuarios. Finalmente, la tabla User_has_Servicios cumple una función operativa, ya que actúa como puente entre Usuario y Servicios, estableciendo una relación de muchos a muchos y registrando los servicios asociados a cada usuario. Esta estructura organiza los datos de manera clara, separando lo esencial de lo complementario y permitiendo un flujo funcional entre las entidades.
<p align="center"> <img width="858" height="619" alt="image" src="https://github.com/user-attachments/assets/0dd771dc-1fd7-4b2e-9e92-11c8d1c60235" /> </p>

  
#### DNS
- **Pi-hole**
  
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
<img width="929" height="359" alt="image" src="https://github.com/user-attachments/assets/fdf91bfc-fad9-4460-afaf-b32d1aa5b022" />



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
  
**DNS**

**DHCP**

**Apache**

**Firewall**

**Copias de seguridad** 


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
