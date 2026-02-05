 Laboratorio01

 

#Estado del Proyecto: En Desarrollo (WIP)

Este repositorio documenta el avance de mi proyecto de laboratorio numero 01, realizado con equipos que fueron prestados amablemente en mi practica profesional, con el fin de aprender y formarme en el ambito practico de mi carrera profesional, para mejorar en campos como SecOps o Infraestructura Segura. Al igual que este proyecto.
tengo otros varios laboratorios que estaré subiendo dentro de las proximas semanas/meses. 

#Hardware
- Switch : Huawei S2720-28TP-PWR-EI
- Router : Cisco - 887M
- Servidor : Proxmox 9.1 (Debian 13) - i3 7th - 8GB RAM DDR4
- Administración : Ubuntu Desktop 24.04 - intel core i5 11th - 12GB RAM DDR4

#Descripción del proyecto

El objetivo es implementar una infraestructura de red endurecida y segura, que sirva como base para un clouster automatizado con distintos servicios Linux con un enfoque en hardening. El proyecto busca garantizar la tríada de la seguridad (Confidencialidad, Integridad y Disponibilidad) mediante:


  -Segmentación, se busca el aislamiento de servicios de importancia, mediante VLANs (210, 220, 230) para así limitar el movimiento lateral.


  -Visibilidad y Monitoreo, se busca implementar servicios de monitoreo para el análisis de tráfico en tiempo real, utilizando herramientas de diagnóstico como Tcpdump y Wireshark para la detección de anomalías en el flujo de datos.


  -Gestión de Vulnerabilidades, despliegue de un entorno de virtualización en Proxmox dedicado al escaneo de activos, auditoría de servicios y endurecimiento de sistemas operativos como Ubuntu 24.04. 



#Problemas Resueltos y Troubleshutting
- Red : Migración de NetworkManager a systemd-networkd para asegurar IP estática en Ubuntu sin interferencias.
- Enrutamiento : Resolución de tráfico ICMP fallido en Proxmox mediante ajuste de tabla de rutas en bridge vmbr210.

#Próximos Pasos
- Configuración de reglas de firewall en Proxmox y Ubuntu.
- Implementación de servicios adicionales en el entorno virtual.
- Documentación final de la topología de red.


