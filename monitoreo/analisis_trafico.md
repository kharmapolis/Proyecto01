# Herramientas de Monitoreo, Análisis de Red
- Aqui propongo herramientas para el analisis de trafico en tiempo real, lo que me ayuda a detectar intruciónes, problemas de seguridad y problemas rutinarios de conectividad sobretodo en L2

## 1. NIVEL FÍSICO Y TRUNK 

 Este comando es para ver el tráfico crudo con etiquetas 802.1Q en la interfaz física
 Útil para confirmar que el Trunk del Huawei está enviando tags

- tcpdump -i enp1s0 -nn vlan
- (Espacio reservado para evidencia - futura ruta al directorio de /evidencia)
 Filtrar específicamente la VLAN de Administración (210) en la troncal
 Asi puedo comprobar si hay problemas de coneccion en el Sw Huawei
 
- tcpdump -i vmbr0 -nn vlan 210
- (Espacio reservado para evidencia - futura ruta al directorio de /evidencia)
 ## 2. NIVEL DE SERVICIO (Validación de Red de Gestión)


 Monitoreo general de la red de administración (VLAN 210 ya desempaquetada de su "Trama Ethernet")
 Aquí validamos el tráfico que llega al Desktop Ubuntu, el cual es usado para administrar.

- tcpdump -i vmbr210 -nn
- (Espacio reservado para evidencia - futura ruta al directorio de /evidencia)

 Filtrar solo ICMP para pruebas de conectividad y latencia
 
- tcpdump -i vmbr210 icmp
- (Espacio reservado para evidencia - futura ruta al directorio de /evidencia)

## 3. SEGURIDAD Y HARDENING (Detección de Anomalías)


Detectaremos intentos de escaneo de puertos (Flags SYN), hacia el Futuro servidor Ubuntu (Aun en desarrollo).
Un flujo alto de estos paquetes podría indicar un escaneo de Nmap externo
- tcpdump -i vmbr210 dst 10.200.10.xxx '

Para limpiar el ruido visual: Ver todo EXCEPTO el tráfico SSH (Puerto 22)
Ideal para no ver tu propia conexión mientras monitoreas el resto

- tcpdump -i vmbr210 -nn not port 22
- (Espacio reservado para evidencia - futura ruta al directorio de /evidencia)
## 4. AUDITORÍA Y CAPTURA (Forense)

 Exportar captura completa a formato .pcap para análisis profundo en Wireshark
 Este archivo es el que luego subiremos como evidencia al portafolio
 
- tcpdump -i vmbr210 -w auditoria_red_admin.pcap
- (Espacio reservado para evidencia - futura ruta al directorio de /evidencia)
