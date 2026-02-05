# Interfaces :
Ethernet 0/0/1 Servidor Proxmox - VLAN 210 \
Ethernet 0/0/2 - administración , desktop Ubuntu - VLAN 210

# PROGRESO ACTUAL DE COMANDOS EN SWITCH HUAWEI S2720 : 
Secuencia : 

- system-view                                     
- vlan 210                                        
- quit                                             
- interface Ethernet 0/0/1          < - - - Puerto Proxmox - Modo Trunk                     
- port link-type trunk                            
- port trunk allow-pass vlan 210                  
- quit                                             
- interface Ethernet 0/0/2          < - - -  Puerto Administración Ubuntu - Modo Access                    
- port link-type access                            
- port default vlan 210                           
- quit                                             
- display vlan 210                  < - - - Verificación, tagged Ethernet 0/0/1 - 2                           
- save                                            

#### (aqui insertaré foto de los comandos de huawei os # display interfaces brief" y # display vlan 210", el dia de mañana 04/02/2026)
