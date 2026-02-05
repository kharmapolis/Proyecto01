# Kit de Herramientas de Monitoreo: Scripts de Análisis de Red

## 1. NIVEL FÍSICO Y TRUNK 


 Ver tráfico crudo con etiquetas 802.1Q en la interfaz física
 Útil para confirmar que el Trunk del Huawei está enviando tags

### tcpdump -i enp1s0 -nn vlan

 Filtrar específicamente la VLAN de Administración (210) en la troncal
 Si aquí no sale nada, el problema está en el Switch físico
tcpdump -i vmbr0 -nn vlan 210

 ## 2. NIVEL DE SERVICIO (Validación de Red de Gestión)


 Monitoreo general de la red de administración (VLAN 210 ya desempaquetada)
 Aquí validamos el tráfico que llega a tu escritorio Ubuntu

### tcpdump -i vmbr210 -nn

 Filtrar solo ICMP para pruebas de conectividad y latencia
 
### tcpdump -i vmbr210 icmp


## 3. SEGURIDAD Y HARDENING (Detección de Anomalías)


Detectar intentos de escaneo de puertos (Flags SYN) hacia el servidor Ubuntu
Un flujo alto de estos paquetes podría indicar un escaneo de Nmap externo
### tcpdump -i vmbr210 dst 10.200.10.50 '

Limpiar el ruido visual: Ver todo EXCEPTO el tráfico SSH (Puerto 22)
Ideal para no ver tu propia conexión mientras monitoreas el resto
tcpdump -i vmbr210 -nn not port 22

## 4. AUDITORÍA Y CAPTURA (Forense)

 Exportar captura completa a formato .pcap para análisis profundo en Wireshark
 Este archivo es el que luego subiremos como evidencia al portafolio
### tcpdump -i vmbr210 -w auditoria_red_admin.pcap
