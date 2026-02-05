
En esta imagen , se aprecia la configuración de la interfaz fisica "nic0", la cual se dividira en dos puentes. \
- "vmbr210" (puente para la administración VLAN 210) \
- "vmbr0" (puente para el gateway y salida WAN) \
  Esta file, será leida por ifupdown2 (herramienta moderna de gestión de interfaces de red, reescrita en Python) para llevar a cabo las operaciónes de red.
  ## Importante : Al activar bridge-vlan-aware, fuerzo a que el tráfico esté etiquetado, evitando que cualquier VM salte a una red que no le corresponde.
 Por el momento, el archivo /interfaces, Coincide perfectamente la configuración de Netplan en Ubuntu y el Trunk en el switch Huawei.
  

<img width="787" height="586" alt="Proxmox_Interfaces" src="https://github.com/user-attachments/assets/14d69571-2ce1-43b2-9e6b-289bf2b071f5" />

#Notas : 
- Las IP's, Gateways nombres de dispositivo y usuario fueron borradas con una herramienta de edición de imagenes para conservar la seguridad de la red en donde se trabaja. 
- Esta es la configuración inicial con la finalidad de poder conectarme a traves de SSH con el Host de administración (Ubuntu Desktop 24.04)

