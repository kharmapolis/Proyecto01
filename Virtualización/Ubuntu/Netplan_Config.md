
# Contenido del archivo netplan en Ubuntu Desktop - Administración : 
network:  \
  version: 2  \
  renderer: networkd   \
  ethernets:  \
    enp4s0:  \
      addresses:  \
        - 10.200.10.50/24

 ![NETPLAN](https://github.com/user-attachments/assets/44cec981-006b-432f-ba57-e4eaac96e70d)

 - Se usa el comando ` sudo chmod 600 xxx.yaml` para dar permisos de lectura y escritura solo al usuario ` root `



 ### Notas
 
  En el archivo de Netplan (Ubuntu) :
- La flag "renderer: networkd " indica cual motor de backend, utilizará el sistema operativo para aplicar y gestionar la configuración de red, en este caso es utilizado para mitigar un conflicto entre el motor Netword y Netwokr_Manager, en este caso se prefiere Networkd ya que permite una configuración mas tecnica, estable y especializada

- No se define el Gateway ni DNS, ya que el servidor aun no necesita salir a internet ni resolver nombres de dominio (Cuando se agregue L3 con el router cisco 800 Series, esta file será actualizada).

- Se debe tener mucho cuidado con las sangrías incorrectas, ya que el formato YAML que usa networkd, es sensible a los espacios, Un solo espacio de más, hará que la configuración falle.
