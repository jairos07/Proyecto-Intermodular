<center>
<h1 style="">Servidor Multitarea</h1>

---
<img src="ies.webp" width="300">


</center>

<style>
@page {
  @bottom-right {
    content: "Jairo Mosteiro – SMR2 | Trabajo Intermodular | 2025";
    font-size: 10pt;
  }
}
</style>


<style>
@page {
  @bottom-center {
    content: counter(page);
  }
}
</style>


<div style="page-break-after: always;"></div>

# Indice:
- [Indice:](#indice)
  - [**Descripcion**](#descripcion)
  - [**Montaje y especificacion de piezas**](#montaje-y-especificacion-de-piezas)
  - [**Software utilizado**](#software-utilizado)
    - [**Servidores Virtualizados**](#servidores-virtualizados)
  - [Ubuntu Server – DNS y DHCP](#ubuntu-server--dns-y-dhcp)
    - [Descripción](#descripción)
    - [Configuración de red del servidor](#configuración-de-red-del-servidor)
    - [Configuración del servidor DHCP](#configuración-del-servidor-dhcp)
    - [Configuración del servidor DNS](#configuración-del-servidor-dns)
  - [Windows Server – Active Directory y GPOs](#windows-server--active-directory-y-gpos)
    - [Descripción](#descripción-1)
    - [Instalación de Windows Server](#instalación-de-windows-server)
    - [Configuración inicial del servidor](#configuración-inicial-del-servidor)
    - [Creación del dominio](#creación-del-dominio)
    - [Unidades Organizativas y Usuarios](#unidades-organizativas-y-usuarios)
    - [Políticas de Grupo (GPOs)](#políticas-de-grupo-gpos)
  - [Windows Client – Unión al dominio y aplicación de GPOs](#windows-client--unión-al-dominio-y-aplicación-de-gpos)
    - [Descripción](#descripción-2)
    - [Configuración del cliente](#configuración-del-cliente)
    - [Verificación de las GPOs en el cliente](#verificación-de-las-gpos-en-el-cliente)
    - [Resultado final](#resultado-final)
  - [Web – Página corporativa con Web4Pro](#web--página-corporativa-con-web4pro)
    - [Descripción](#descripción-3)
    - [Layout de la página](#layout-de-la-página)
  - [**Conclusion**](#conclusion)
  - [**Glosario**](#glosario)
    - [Hardware](#hardware)
    - [Ubuntu server](#ubuntu-server)
    - [Windows server](#windows-server)

<div style="page-break-after: always;"></div>

## **Descripcion** 

- Este proyecto consiste en el diseño e implementación de un servidor multitarea orientado a pequeñas y medianas empresas (PYMES), cuyo objetivo principal es ofrecer una solución integral, económica y funcional para la gestión de los servicios básicos de una red empresarial.

- La infraestructura del servidor se compone de varios sistemas y servicios que trabajan de forma conjunta. En primer lugar, se utiliza un servidor basado en Ubuntu Server, encargado de proporcionar los servicios de DNS (Domain Name System) y DHCP (Dynamic Host Configuration Protocol). Estos servicios permiten, respectivamente, la correcta resolución de nombres dentro de la red y la asignación automática de direcciones IP a los dispositivos conectados, facilitando así la administración y organización de la red interna de la empresa.

- Además, el proyecto incorpora un servidor Windows Server sobre el cual se configura Active Directory Domain Services (AD DS) junto con Políticas de Grupo (GPOs), que permiten gestionar de forma centralizada los equipos y usuarios que forman parte del dominio empresarial.

- Un aspecto destacado del proyecto es que todo el hardware utilizado es de segunda mano o reciclado, lo que reduce significativamente los costes de implementación y fomenta la sostenibilidad y el aprovechamiento de recursos. De este modo, el servidor se presenta como una alternativa accesible para pequeñas empresas que no disponen de un gran presupuesto tecnológico.

- En conjunto, este servidor multitarea permite a la empresa que lo implemente disponer de gestión de red, servicios web, bases de datos y seguridad, todo centralizado en una única infraestructura, contribuyendo a mejorar la eficiencia, el control y la fiabilidad de su entorno informático.

<div style="page-break-after: always;"></div>

## **Montaje y especificacion de piezas**

- Las piezas que componen este servidor han sido recicladas de otros equipos informáticos o adquiridas de segunda mano. Es importante destacar este aspecto, ya que optar por este tipo de soluciones contribuye a un futuro más sostenible, reduciendo la generación de residuos electrónicos y fomentando la reutilización de hardware que aún se encuentra en buen estado de funcionamiento.

- Además del impacto positivo a nivel medioambiental, el uso de componentes reciclados supone una reducción significativa de costes en comparación con la compra de hardware nuevo. Para pequeñas y medianas empresas, este factor resulta clave, ya que permite disponer de una infraestructura funcional sin necesidad de realizar una gran inversión inicial. Si los componentes cumplen correctamente su función y no presentan problemas de rendimiento o estabilidad, darles una segunda vida útil es una opción totalmente válida y recomendable.

- El equipo servidor cuenta con los siguientes componentes principales:

- Unidad de almacenamiento SSD de 500 GB, destinada al sistema operativo y a los servicios principales, lo que garantiza tiempos de arranque rápidos y un buen rendimiento general.

- Procesador AMD Ryzen 5 3400G, que ofrece un equilibrio adecuado entre potencia y eficiencia energética, siendo suficiente para tareas de servidor, virtualización ligera y servicios de red.

- 32 GB de memoria RAM DDR4, cantidad más que adecuada para soportar múltiples servicios simultáneos y garantizar la estabilidad del sistema.

- Fuente de alimentación (PSU) de 750 W con certificación 80 Plus Bronze, que asegura una eficiencia energética aceptable y un suministro eléctrico estable para todos los componentes.

- Placa base Gigabyte GA-AB350-Gaming 3, compatible con el procesador utilizado y adecuada para la ampliación y reutilización en entornos de laboratorio o servidor.

- Para facilitar la identificación y comprensión del hardware empleado, se adjuntan imágenes de todos los componentes principales del equipo en el apartado de [**Glosario**](#glosario) de este proyecto.

- Por último, el gabinete del servidor ha sido reutilizado de un ordenador antiguo que iba a ser desechado. De este modo, se ha intentado aprovechar al máximo las piezas disponibles que dicho equipo podía ofrecer, reforzando aún más la filosofía de reutilización y sostenibilidad que caracteriza a este proyecto.

<div style="page-break-after: always;"></div>

## **Software utilizado**

- El SO utilizado en este servidor es Proxmox y tomé esta decisión basándome en la facilidad para instalar herramientas y porque suelo tener más afinidad con la shell de Linux que con el CMD de Windows, y porque me parecía una opción más realista a la hora de lo que verdaderamente se utiliza en el mundo empresarial.

  ### **Servidores Virtualizados**
  
  En este apartado hablaré sobre los servidores virtualizados que tenemos en nuestro servidor principal y el porqué he escogido cada uno de estos para cada tarea.

<div style="page-break-after: always;"></div>

---

## Ubuntu Server – DNS y DHCP

### Descripción

Ubuntu Server es el sistema operativo elegido para gestionar los servicios de red más básicos pero fundamentales de la infraestructura: **DNS** y **DHCP**. La elección de Ubuntu Server se debe a su estabilidad, su amplia comunidad de soporte, la facilidad de administración mediante terminal y la disponibilidad de paquetes como `bind9` (DNS) e `isc-dhcp-server` (DHCP) en sus repositorios oficiales.

- El servicio **DHCP** permite que cualquier equipo que se conecte a la red empresarial reciba automáticamente una dirección IP, máscara de subred, puerta de enlace y servidor DNS, eliminando la necesidad de configuración manual en cada dispositivo.

- El servicio **DNS** permite traducir nombres de dominio a direcciones IP y viceversa, facilitando la comunicación dentro de la red interna y el acceso a Internet.

---

### Configuración de red del servidor

Antes de instalar los servicios, se configuró una IP estática en el servidor Ubuntu para que siempre sea accesible desde la misma dirección dentro de la red.

<img src="ubuntu-server/conf1.png">

> Configuración inicial de la interfaz de red del servidor Ubuntu.

<img src="ubuntu-server/conf2.png">

> Verificación de la interfaz y asignación de IP estática mediante Netplan.

<img src="ubuntu-server/conf3.png">

> Aplicación de la configuración de red con `netplan apply`.

<img src="ubuntu-server/conf4.png">

> Comprobación de conectividad y resolución de nombres tras aplicar la configuración.

<img src="ubuntu-server/conf5.png">

> Estado final de la interfaz de red con la IP estática asignada correctamente.

---

### Configuración del servidor DHCP

Para la instalación del servicio DHCP se utilizó el paquete `isc-dhcp-server`. Se configuró el rango de IPs que se asignarán automáticamente a los clientes, la puerta de enlace, el DNS y el tiempo de concesión.

<img src="ubuntu-server/dhcp1.png">

> Configuración del archivo `/etc/dhcp/dhcpd.conf` con el rango de IPs, la subred y los parámetros de red entregados a los clientes.

<img src="ubuntu-server/dhcp2.png">

> Inicio y verificación del estado del servicio `isc-dhcp-server` para confirmar que está activo y funcionando correctamente.

---

### Configuración del servidor DNS

Para el servidor DNS se instaló el paquete `bind9`. Se configuraron las zonas directa e inversa para el dominio interno de la empresa, de modo que los equipos puedan resolver nombres internos y también tener salida a Internet.

<img src="ubuntu-server/dns1.png">

> Instalación del paquete `bind9` y utilidades asociadas.

<img src="ubuntu-server/dns2.png">

> Configuración del archivo `/etc/bind/named.conf.local` con la declaración de las zonas directa e inversa.

<img src="ubuntu-server/dns3.png">

> Configuración del archivo `/etc/bind/named.conf.options` con los reenviadores DNS (forwarders) para la resolución externa.

<img src="ubuntu-server/dns4.png">

> Creación del archivo de zona directa con los registros A, NS y CNAME necesarios.

<img src="ubuntu-server/dns5.png">

> Creación del archivo de zona inversa con los registros PTR para la resolución inversa.

<img src="ubuntu-server/dns6.png">

> Verificación de la sintaxis de los archivos de zona con `named-checkzone`.

<img src="ubuntu-server/dns7.png">

> Reinicio del servicio `bind9` y comprobación de su estado.

<img src="ubuntu-server/dns8.png">

> Prueba de resolución DNS directa con el comando `nslookup` desde un cliente.

<img src="ubuntu-server/dns9.png">

> Prueba de resolución DNS inversa, comprobando que una IP se traduce correctamente al nombre del host.

<img src="ubuntu-server/dns10.png">

> Verificación final de conectividad completa entre cliente y servidor usando los servicios DNS y DHCP configurados.

<div style="page-break-after: always;"></div>

---

## Windows Server – Active Directory y GPOs

### Descripción

Windows Server es el sistema operativo utilizado para gestionar el entorno de directorio activo de la empresa. Mediante **Active Directory Domain Services (AD DS)** se centraliza la autenticación y autorización de todos los usuarios y equipos de la red. Las **Políticas de Grupo (GPOs)** permiten aplicar configuraciones de seguridad, restricciones y personalizaciones de forma automatizada a todos los equipos del dominio.

La elección de Windows Server para este rol se debe a que es el estándar de la industria para entornos empresariales basados en Windows, y su integración nativa con Active Directory lo convierte en la opción más coherente para gestionar un dominio de equipos Windows.

---

### Instalación de Windows Server

<img src="Windows-server/instalacion1.png">

> Proceso de instalación de Windows Server. Se selecciona la versión con experiencia de escritorio para facilitar la administración visual.

<img src="Windows-server/instalacion2.png">

> Finalización de la instalación y primer inicio del sistema operativo.

---

### Configuración inicial del servidor

<img src="Windows-server/config1.png">

> Configuración de la IP estática del servidor Windows Server. Es imprescindible que el servidor tenga siempre la misma IP para que los clientes puedan localizarlo en la red.

<img src="Windows-server/config2.png">

> Configuración del nombre del servidor y verificación de la conectividad de red antes de proceder con la instalación del rol de Active Directory.

---

### Creación del dominio

<img src="Windows-server/dominio1.png">

> Instalación del rol **Active Directory Domain Services** desde el Administrador del Servidor. Este rol es el núcleo de toda la infraestructura de directorio.

<img src="Windows-server/dominio2.png">

> Promoción del servidor a **Controlador de Dominio** y creación del nuevo bosque/dominio. Se especifica el nombre del dominio interno de la empresa (por ejemplo, `empresa.local`).

---

### Unidades Organizativas y Usuarios

<img src="Windows-server/Unidad-organizativa1.png">

> Creación de **Unidades Organizativas (OUs)** en Active Directory Users and Computers. Las OUs permiten organizar los objetos del directorio (usuarios, equipos, grupos) de forma jerárquica, facilitando la aplicación de GPOs específicas a cada departamento o grupo.

<img src="Windows-server/usuarios1.png">

> Creación de cuentas de usuario dentro de las Unidades Organizativas correspondientes. Cada usuario tiene sus credenciales de acceso al dominio y pertenece al grupo o departamento adecuado.

<img src="Windows-server/usuarios2.png">

> Verificación de los usuarios creados y sus propiedades: grupo de pertenencia, ruta de perfil y configuración de contraseña.

---

### Políticas de Grupo (GPOs)

<img src="Windows-server/GPO1.png">

> Creación de una nueva **GPO (Group Policy Object)** desde la Consola de Administración de Directivas de Grupo (GPMC). La GPO se vincula a la Unidad Organizativa correspondiente para que se aplique a todos los equipos y usuarios de ese contenedor.

<img src="Windows-server/GPO2.png">

> Edición de la GPO con las políticas de seguridad y configuración deseadas: restricciones de escritorio, configuración de fondo de pantalla corporativo, bloqueo de acceso al panel de control, entre otras. Estas políticas se aplicarán automáticamente cada vez que un usuario inicie sesión en un equipo del dominio.

<div style="page-break-after: always;"></div>

---

## Windows Client – Unión al dominio y aplicación de GPOs

### Descripción

El cliente Windows es un equipo de escritorio que se une al dominio creado en Windows Server. Una vez integrado en el dominio, el cliente recibe automáticamente las Políticas de Grupo configuradas en el servidor, permitiendo una gestión centralizada de su configuración y seguridad sin necesidad de intervención manual en cada equipo.

---

### Configuración del cliente

<img src="Windows-client/Config1.png">

> Configuración del cliente Windows para que utilice la IP del servidor Windows Server como **DNS primario**. Este paso es imprescindible para que el cliente pueda resolver el nombre del dominio y unirse a él.

<img src="Windows-client/config2.png">

> Proceso de **unión al dominio** desde el cliente: en Propiedades del Sistema se especifica el nombre del dominio (`empresa.local`) y se introducen las credenciales de un administrador del dominio para autorizar la unión.

---

### Verificación de las GPOs en el cliente

<img src="Windows-client/GPO3.png">

> Comprobación de las GPOs aplicadas en el cliente mediante el comando `gpresult /r`. Se puede observar que las políticas definidas en el servidor se han aplicado correctamente al equipo cliente tras su incorporación al dominio.

---

### Resultado final

<img src="Windows-client/resultado1.png">

> Resultado final: el cliente ha iniciado sesión correctamente con un usuario del dominio y se observa que las políticas de grupo están activas (fondo de pantalla corporativo, restricciones configuradas, etc.), confirmando que toda la infraestructura de Active Directory funciona correctamente de extremo a extremo.

<div style="page-break-after: always;"></div>

---

## Web – Página corporativa con Web4Pro

### Descripción

Como parte del proyecto, se desarrolla una página web corporativa utilizando el CMS **Web4Pro**. Este gestor de contenidos permite crear y administrar páginas web de forma sencilla y profesional, sin necesidad de programar desde cero, adaptándose perfectamente a las necesidades de una pequeña o mediana empresa.

La página web de la empresa es de acceso público y puede visitarse buscando **"piezasdeinformatica"** en cualquier navegador.

---

### Layout de la página

<img src="WEB/layout.png">

> Vista general del layout de la página web corporativa, donde se puede apreciar la estructura y disposición de los elementos que componen la web.

<div style="page-break-after: always;"></div>

---

## **Conclusion**

Este proyecto ha supuesto la puesta en práctica de numerosos conocimientos adquiridos a lo largo del ciclo formativo de Sistemas Microinformáticos y Redes, integrando tanto hardware como software en una infraestructura real y funcional.

Desde el montaje físico del servidor con componentes reciclados hasta la configuración de servicios de red avanzados, cada fase del proyecto ha presentado sus propios retos y aprendizajes:

- La configuración del **servidor Ubuntu** con DNS y DHCP me permitió profundizar en la administración de sistemas Linux, en el funcionamiento de los protocolos de red y en la importancia de una correcta planificación del direccionamiento IP en una red empresarial.

- La implementación de **Active Directory** en Windows Server fue especialmente significativa, ya que es una tecnología ampliamente utilizada en el mundo laboral. Comprender cómo funciona la gestión centralizada de usuarios, equipos y políticas me ha dado una perspectiva más clara de cómo se administran las redes empresariales reales.

- El desarrollo de la **página web** con un CMS en mi estadia en la empresa me ayudo a ganar experiencia en el ambito de el desarroyp web.

- El uso de **hardware reciclado** no solo supuso un ahorro económico considerable, sino que también reforzó la conciencia sobre la sostenibilidad en el sector tecnológico.

En resumen, este proyecto representa una solución integral, realista y económica que podría perfectamente ser implantada en una pequeña o mediana empresa, cumpliendo con los requisitos de gestión de red, seguridad, presencia web y administración centralizada de usuarios.

<div style="page-break-after: always;"></div>

## **Glosario**

### Hardware

A continuación se muestran imágenes del hardware utilizado en el servidor. Todos los componentes han sido reciclados o adquiridos de segunda mano, manteniendo un funcionamiento óptimo.

<img src="Hardware/IMG_2316.jpg">

> Vista general del interior del equipo servidor con los componentes montados.

<img src="Hardware/IMG_2317.jpg">

> Detalle de la placa base Gigabyte GA-AB350-Gaming 3 con el procesador AMD Ryzen 5 3400G instalado.

<img src="Hardware/IMG_2318.jpg">

> Módulos de memoria RAM DDR4 instalados en la placa base (32 GB en total).

<img src="Hardware/IMG_2319.jpg">

> Vista del conjunto completo: fuente de alimentación 750W 80 Plus Bronze, SSD de 500 GB y cableado interno del equipo.

---

### Ubuntu server

| Término | Definición |
|---|---|
| **DHCP** | Dynamic Host Configuration Protocol. Protocolo que asigna automáticamente configuración de red (IP, máscara, gateway, DNS) a los dispositivos conectados. |
| **DNS** | Domain Name System. Sistema que traduce nombres de dominio legibles (ej: `servidor.empresa.local`) a direcciones IP numéricas. |
| **Bind9** | Implementación de servidor DNS más utilizada en sistemas Linux/Unix. |
| **isc-dhcp-server** | Paquete de servidor DHCP para sistemas Linux, desarrollado por el Internet Systems Consortium. |
| **Netplan** | Herramienta de configuración de red en Ubuntu que utiliza archivos YAML para definir interfaces y sus parámetros. |
| **Zona directa** | Archivo de zona DNS que resuelve nombres a IPs (registro A). |
| **Zona inversa** | Archivo de zona DNS que resuelve IPs a nombres (registro PTR). |
| **Forwarder** | Servidor DNS externo al que se reenvían las consultas que el servidor local no puede resolver (ej: 8.8.8.8 de Google). |

---

### Windows server

| Término | Definición |
|---|---|
| **Active Directory (AD)** | Servicio de directorio de Microsoft que centraliza la gestión de usuarios, equipos y recursos en una red Windows. |
| **Controlador de Dominio (DC)** | Servidor que ejecuta Active Directory y autentica a los usuarios y equipos del dominio. |
| **Dominio** | Conjunto de equipos y usuarios que comparten una base de datos de directorio común y políticas de seguridad centralizadas. |
| **GPO** | Group Policy Object. Objeto que contiene una o más configuraciones de directiva de grupo que se aplican a usuarios y equipos del dominio. |
| **OU (Unidad Organizativa)** | Contenedor de Active Directory que agrupa objetos (usuarios, equipos, grupos) para facilitar su administración y la aplicación de GPOs. |
| **GPMC** | Group Policy Management Console. Herramienta de administración para crear, editar y vincular GPOs en el dominio. |
| **gpresult** | Comando de Windows que muestra las GPOs aplicadas a un usuario o equipo concreto. |

