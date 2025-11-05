# SICMA

## Índice
1. Introducción
2. Briefing de ideas
3. Arquitectura del software
4. Tecnologías a utilizar
5. Red
   - Diagrama de la red
   - Mapa físico
   - Mapa lógico
6. Web
   - Diseño
   - Mockup
   - Mapa de navegabilidad
7. Servicios
   - DNS
   - DHCP
   - Apache
   - Firewall
   - Copias de seguridad
8. Conclusiones
9. Bibliografía

---

## 1. Introducción
SICMA es una plataforma web destinada a la gestión y control de los servicios de limpieza de una empresa. Su propósito es mejorar la organización del personal, la administración de tareas y la supervisión de los trabajos realizados en diferentes instalaciones.  
El sistema pretende optimizar los procesos internos, garantizando una comunicación eficiente entre responsables y operarios, así como un registro claro de las actividades ejecutadas.

---

## 2. Briefing de ideas
El proyecto surge de la necesidad de digitalizar y centralizar la gestión del servicio de limpieza, evitando procesos manuales y lentos.  
Mediante la implementación de SICMA, se busca:

- Reducir errores en la asignación de tareas
- Automatizar la planificación del personal
- Mantener registros actualizados de trabajos finalizados
- Mejorar el control de calidad del servicio

El resultado final debe ser un sistema accesible, simple y funcional.

---

## 3. Arquitectura del software
SICMA se organiza bajo una arquitectura cliente-servidor.

- **Frontend**: interfaz web para empleados y administradores
- **Backend**: servidor encargado de la lógica de negocio y gestión de datos
- **Base de datos**: almacenamiento de usuarios, tareas, ubicaciones y reportes

El sistema se basa en una separación clara entre presentación, lógica y datos, permitiendo una futura escalabilidad.

---

## 4. Tecnologías a utilizar
| Componente | Tecnología |
|-----------|------------|
| Frontend | HTML5, CSS3, JavaScript |
| Backend | PHP |
| Base de datos | MySQL |
| Servidor Web | Apache2 |
| Control de versiones | Git / GitHub |
| Sistema operativo servidor | Linux |

---

## 5. Red

#### Diagrama de la red
Representa la interconexión entre el servidor web, el servidor de base de datos, los clientes y los equipos administrativos, asegurando una comunicación interna segura.

#### Mapa físico
Consta de los dispositivos y su ubicación real:
- Router principal
- Conexiones cableadas para los equipos internos
- Servidor ubicado en una zona segura

#### Mapa lógico
Estructura de la red interna:
- Segmentación por subredes
- Rango de direcciones IP definidas
- Control de acceso mediante firewall

---

## 6. Web

#### Diseño
El diseño se basa en una estructura simple y accesible:
- Colores neutros que transmiten limpieza
- Menús claros y visibles
- Interfaz intuitiva enfocada en la productividad

#### Mockup
Representación visual previa de la plataforma para definir:
- Distribución de elementos
- Pantallas de acceso, panel administrativo y tareas

#### Mapa de navegabilidad
Flujo de navegación:
- Ingreso al sistema → Panel de control
- Gestión de empleados, tareas y ubicaciones
- Cierre y envío de reportes

---

## 7. Servicios

#### DNS
Configuración de un nombre de dominio interno para acceder al sistema de forma cómoda por parte de los empleados autorizados.

#### DHCP
Asignación automática de direcciones IP a los equipos conectados en la red.

#### Apache
Servidor encargado de alojar y distribuir la página web SICMA al navegador del usuario.

#### Firewall
Reglas configuradas para permitir únicamente los puertos y conexiones requeridas por el servicio web, protegiendo contra accesos no autorizados.

#### Copias de seguridad
Copias periódicas de la base de datos con el fin de garantizar la integridad de la información ante cualquier fallo o incidente.

---

## 8. Conclusiones
SICMA ofrece una solución moderna y eficiente para el control del servicio de limpieza dentro de una empresa. Permite reducir costos operativos, mejorar la coordinación del personal y obtener un seguimiento detallado del trabajo realizado.  
Su estructura modular facilita futuras ampliaciones y la integración de nuevas funcionalidades según las necesidades de la organización.

---

## 9. Bibliografía
- Manuales oficiales de PHP, MySQL y Apache
- Documentación de estándares web HTML5 y CSS3
- Recursos de administración de redes y seguridad informática

