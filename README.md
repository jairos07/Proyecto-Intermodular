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

┌──────────────────────────────────────────────────────────────────────────┐
│                      ARQUITECTURA DEL PROYECTO                           │
└──────────────────────────────────────────────────────────────────────────┘

                            INTERNET (WAN)
                                  │
                    ┌─────────────▼─────────────┐
                    │    pfSense Firewall       │
                    │    Reglas de Seguridad    │
                    │    - DNS (port 53)        │
                    │    - DHCP (port 67-68)    │
                    │    - SSH (port 22)        │
                    │    - Block Internet       │
                    └─────────────┬─────────────┘
                                  │
                    ┌─────────────▼────────────────────────┐
                    │    PROXMOX HYPERVISOR                │
                    │    (192.168.1.100)                   │
                    │                                      │
                    │  ┌──────────────────────────────┐   │
                    │  │  Ubuntu Server               │   │
                    │  │  192.168.100.100             │   │
                    │  │  ✓ DNS (bind9)               │   │
                    │  │  ✓ DHCP (isc-dhcp-server)    │   │
                    │  └──────────────────────────────┘   │
                    │                                      │
                    │  ┌──────────────────────────────┐   │
                    │  │  Windows Server - AD         │   │
                    │  │  192.168.100.101             │   │
                    │  │  ✓ Active Directory          │   │
                    │  │  ✓ GPOs                      │   │
                    │  └──────────────────────────────┘   │
                    │                                      │
                    │  ┌──────────────────────────────┐   │
                    │  │  Ubuntu LAB (x3)             │   │
                    │  │  192.168.1.110-.112          │   │
                    │  │  ✓ Creadas por Ansible       │   │
                    │  └──────────────────────────────┘   │
                    │                                      │
                    └──────────────────────────────────────┘
                                  ▲
                                  │
                    ┌─────────────┴─────────────┐
                    │   ANSIBLE AUTOMATION      │
                    │                           │
                    │   ✓ Playbooks             │
                    │   ✓ Inventory             │
                    │   ✓ SSH a Proxmox         │
                    └───────────────────────────┘

## Contenidos del Repositorio

##  Contenidos del Proyecto

### 1. pfSense Firewall
- Instalación en Proxmox
- Configuración de interfaces 
- Reglas de firewall (DNS, DHCP, SSH, Internal)
- Logging de eventos
- Topología: aislamiento de red + control de tráfico

### 2. Ubuntu Server - Servicios de Red
- DNS (bind9) - resolución de nombres smr.local
- DHCP (isc-dhcp-server) - asignación de IPs 192.168.100.0/24
- Configuración Netplan - IP estática 192.168.100.100
- Verificación con nslookup y dhclient

### 3. Windows Server - Active Directory
- Instalación y configuración de AD DS
- Creación de dominio server.local
- Unidades Organizativas (OUs)
- Usuarios y grupos de seguridad
- Políticas de Grupo (GPOs) - personalización corporativa
- Windows Client unido al dominio

### 4. Ansible - Infraestructura como Código (IaC)
- Automatización de creación de VMs en Proxmox
- Playbook: ubuntu-vms.yml (3 máquinas en paralelo)
- Inventory: configuración de proxmox.yml
- Resultado: 3 VMs en 5 minutos vs 45 minutos manual
- Reducción de tiempo: 80%

###  Arquitectura Completa
- Proxmox como hipervisor
- pfSense como firewall perimetral
- Ubuntu Server como hub de servicios de red
- Windows AD como gestión centralizada
- Ansible como motor de automatización

###  Competencias Demostradas
✓ Virtualización (Proxmox/KVM)
✓ Administración de Linux (DNS, DHCP)
✓ Directorio Activo y GPOs
✓ Seguridad de red (firewall, reglas)
✓ Infrastructure as Code (Ansible/YAML)
✓ Documentación técnica

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

#### 4. Firewall Pfsense
- Configuracion de firewall pfsense
- Reglas custom
- Loggin de eventos
- Configuraccion de adaptadores

#### 5.Ansible
- Automatización de creación de VMs en Proxmox
- Playbook: ubuntu-vms.yml (3 máquinas en paralelo)
- Inventory: configuración de proxmox.yml

#### 6. Página Web Corporativa
- Implementación con Web4Pro CMS
- Layout corporativo profesional
- Búsqueda disponible en "piezasdeinformatica"

## Cómo desplegar los servicios

### Requisitos
- Proxmox (o virtualización similar)
- Ubuntu Server 20.04 LTS o superior
- Windows Server 2019/2022
- Windows 10/11 para cliente
- pfsense para firewall
- Software ansible + conectarlo a proxmox


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
- Firewall funcional 
- Automatizaciones para optimizacion de tiempo
- Fácil mantenimiento y escalabilidad

## Aprendizajes Clave

1. Administración de sistemas Linux (Ubuntu Server)
2. Configuración de servicios de red (DNS, DHCP)
3. Implementación de Active Directory
4. Gestión de Políticas de Grupo en Windows
5. Gestion y instalacion de firewall pfsense
6. Planificación de infraestructura IT empresarial
7. Importancia de la documentación técnica
8. Sostenibilidad en tecnología

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

