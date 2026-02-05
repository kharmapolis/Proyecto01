# Proyecto n° 01 - en desarrollo
## Fecha de incio : 10/01/2026
## Estado del Proyecto

🟡 Actual: VLAN 210 y red de administración operativa  
🟢 En progreso: Implementación de gateway con pfSense  
⚪ Planificado: VLAN 220 (Servidores), VLAN 230 (DMZ), reglas de seguridad

Este repositorio documenta tanto la implementación actual como el diseño objetivo del laboratorio.

Este repositorio documenta el avance de mi proyecto de laboratorio número 01, realizado con equipos que me fueron facilitados amablemente en mi práctica profesional, con el fin de aprender y formarme en el ámbito práctico de mi carrera profesional, para mejorar en campos como AdmSYS y Network Management con una orientación hacia SecOps. Al igual que este proyecto, tengo otros varios laboratorios que estaré completando y compartiendo dentro de las próximas semanas/meses.

### Índice:
#### Estructura: 
 - [Hardware y SO](./Planificación/Hardware.md) 
 - [Diagrama de red](./Planificación/Estructura/Diagrama_Mermaid.md) 
#### Archivos de Configuración y monitoreo de red: 
 - [Configuración de Netplan (Ubuntu Desktop Administración)](./Virtualización/Ubuntu/Netplan_Config.md) 
 - [Configuración de VLANs (Switch Huawei)](./networking/huawei/Config_Huawei.md) 
 - [Interfaces y Bridges (Proxmox)](./Virtualización/Proxmox/Proxmox_Interfaces.md) 
 - [Toolkit de Monitoreo (Tcpdump)](./monitoreo/analisis_trafico.md)
#### Mejoras en camino: 


# Notas sobre la metodología de Aprendizaje: 
Este proyecto se enfoca en el uso de herramientas elementales y configuraciones manuales. El objetivo es reducir la abstracción de manera deliberada para demostrar y comprender los conceptos fundamentales de networking y seguridad de forma tangible. Al interactuar directamente con la base técnica, puedo garantizar un aprendizaje real y profundo, permitiendo que la transición hacia herramientas automatizadas sea más sólida y consciente


# Descripción del proyecto:

El objetivo es implementar una infraestructura de red endurecida y segura, que sirva como base para un clúster automatizado con distintos servicios Linux con un enfoque en hardening. El proyecto busca garantizar la tríada de la seguridad (Confidencialidad, Integridad y Disponibilidad) mediante:

    Segmentación: se busca el aislamiento de servicios de importancia, mediante VLANs (210, 220, 230) para así limitar el movimiento lateral.

    Visibilidad y Monitoreo: se busca implementar servicios de monitoreo para el análisis de tráfico en tiempo real, utilizando herramientas de diagnóstico como Tcpdump y Wireshark para la detección de anomalías en el flujo de datos.

    Gestión de Vulnerabilidades: despliegue de un entorno de virtualización en Proxmox dedicado al escaneo de activos, auditoría de servicios y endurecimiento de sistemas operativos como Ubuntu 24.04.

# Problemas Resueltos y Troubleshutting:
- Red : Migración de NetworkManager a systemd-networkd para asegurar IP estática en Ubuntu sin interferencias.
- Enrutamiento : Resolución de tráfico ICMP fallido en Proxmox mediante ajuste de tabla de rutas en bridge vmbr210.




