
# Contenido del archivo netplan en Ubuntu Desktop - Administración : 
network:  \
  version: 2  \
  renderer: networkd  # Ignorar NetworkManager  \
  ethernets:  \
    enp4s0:  \
      addresses:  \
        - 10.200.10.50/24

 ![NETPLAN](https://github.com/user-attachments/assets/44cec981-006b-432f-ba57-e4eaac96e70d)



 
En el archivo de Netplan (Ubuntu)

  #No se define el Gateway ni DNS, ya que el servidor aun no necesita salir a internet ni resolver nombres de dominio.

  #Tuve mucho cuidado con las sangrías incorrectas, YAML es extremadamente sensible a los espacio Un solo espacio de más en addresses hará que la configuración falle.
