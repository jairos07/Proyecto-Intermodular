# Servidor Multitarea - Proyecto SMR2

Una solución integral de infraestructura IT para pequeñas y medianas empresas (PYMES), implementada con hardware reciclado y componentes de segunda mano.

## Descripción del Proyecto

Este proyecto implementa un servidor multitarea completo que proporciona:

- Servicios de Red: DNS (bind9) y DHCP (isc-dhcp-server) en Ubuntu Server
- Directorio Activo: Active Directory Domain Services (AD DS) en Windows Server
- Políticas de Grupo: GPOs para gestión centralizada de usuarios y equipos
- Presencia Web: Página corporativa con Web4Pro
- Seguridad: Firewall con pfSense
- Sostenibilidad: Componentes 100% reciclados y de segunda mano

## Componentes Hardware

| Componente | Especificación |
|-----------|----------------|
| Procesador | AMD Ryzen 5 3400G |
| Memoria RAM | 32 GB DDR4 |
| Almacenamiento | SSD 500 GB |
| Fuente | 750W 80 Plus Bronze |
| Placa Base | Gigabyte GA-AB350-Gaming 3 |
| Gabinete | Reciclado de equipo antiguo |

## Arquitectura del Proyecto

├─────────────────────────────────────────┐
│       PROXMOX (Hipervisor)              │
├─────────────────────────────────────────┤
│                                         │
│  ├──────────────────┐  ├─────────────┐ │
│  │ Ubuntu Server    │  │ Windows     │ │
│  │ (DNS + DHCP)     │  │ Server (AD) │ │
│  │ 192.168.100.100  │  │   (DC)      │ │
│  └──────────────────┘  └─────────────┘ │
│         │                     │         │
│         └─────────────────────┘         │
│                 │                       │
│         ├───────┴────────┐              │
│         │  Windows       │              │
│         │  Client        │              │
│         │  (Unido a AD)  │              │
│         └────────────────┘              │
│                                         │
└─────────────────────────────────────────┘

## Contenidos del Repositorio

### Documentación
- `Proyecto_Jairo_Mosteiro_Campos.pdf` - Documento oficial completo del proyecto

### Secciones Principales

#### 1. Ubuntu Server - DNS y DHCP
- Configuración de red estática con Netplan
- Instalación y configuración de bind9 (DNS)
- Instalación y configuración de isc-dhcp-server (DHCP)
- Zonas directa e inversa
- Forwarders para resolución externa
- Pruebas de conectividad

#### 2. Windows Server - Active Directory
- Instalación de Windows Server con escritorio
- Configuración inicial de red
- Promoción a Controlador de Dominio
- Creación de dominio (empresa.local)
- Unidades Organizativas (OUs)
- Creación de usuarios de dominio
- Configuración de Políticas de Grupo (GPOs)

#### 3. Windows Client - Unión al Dominio
- Configuración de DNS primario (servidor AD)
- Proceso de unión al dominio
- Verificación de GPOs aplicadas
- Validación de políticas de seguridad

#### 4. Página Web Corporativa
- Implementación con Web4Pro CMS
- Layout corporativo profesional
- Búsqueda disponible en "piezasdeinformatica"

## Cómo Usar Este Proyecto

### Requisitos
- Proxmox (o virtualización similar)
- Ubuntu Server 20.04 LTS o superior
- Windows Server 2019/2022
- Windows 10/11 para cliente

### Instalación Rápida

1. **Ubuntu Server - DNS y DHCP**

```bash
sudo apt update
sudo apt install bind9 bind9-utils isc-dhcp-server

# Configurar archivos según documentación
sudo systemctl restart bind9
sudo systemctl restart isc-dhcp-server
```

2. **Windows Server - Active Directory**
- Seguir instalación desde GUI (Server Manager)
- Promocionar a DC
- Configurar GPOs según necesidades

3. **Windows Client**
- Configurar DNS -> IP del servidor AD
- Unirse al dominio
- Validar con `gpresult /r`

## Funcionalidades Implementadas

- Asignación automática de IPs (DHCP)
- Resolución de nombres internos (DNS)
- Gestión centralizada de usuarios (AD)
- Aplicación automática de políticas de seguridad (GPOs)
- Aislamiento de recursos por departamento (OUs)
- Página web corporativa públicamente accesible

## Sostenibilidad

Este proyecto demuestra que es posible implementar una infraestructura empresarial profesional utilizando:

- Hardware reciclado y de segunda mano
- Componentes que mantienen rendimiento óptimo
- Reducción significativa de costes de implementación
- Menor impacto ambiental

Ahorro estimado: ~70% vs. soluciones nuevas equivalentes

## Resultados

- Infraestructura completa y funcional
- Todas las pruebas de conectividad correctas
- GPOs aplicadas correctamente en clientes
- Servicios estables y en producción
- Fácil mantenimiento y escalabilidad

## Aprendizajes Clave

1. Administración de sistemas Linux (Ubuntu Server)
2. Configuración de servicios de red (DNS, DHCP)
3. Implementación de Active Directory
4. Gestión de Políticas de Grupo en Windows
5. Planificación de infraestructura IT empresarial
6. Importancia de la documentación técnica
7. Sostenibilidad en tecnología

## Documentación Técnica

Consulta el archivo PDF incluido para detalles completos sobre:
- Especificaciones técnicas
- Pasos de configuración detallados
- Capturas de pantalla de cada proceso
- Glosario de términos técnicos
- Imágenes del hardware utilizado

## Autor

Jairo Mosteiro Campos
Estudiante de SMR2 (Sistemas Microinformáticos y Redes)
IES Lois Peña Novo - 2026

---

