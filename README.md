
# 🔥 Instalar VIRTUAL apta para el MU.

## Requisitos: 
* Última versión de Windows 10 ISO [(Descargar acá)](https://www.microsoft.com/en-gb/software-download/windows10ISO) / Windows 11 ISO [(Descargar acá)](https://www.microsoft.com/en-us/software-download/windows11) - 
* Activar Hyper V en W10/W11 (requiere reiniciar).  
Sino ejecutar este comando en cmd o powershell:    
**Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-Hyper-V -All**  

**⚠️ Importante:** 

* La versión que es **Windows Home** es necesario instalarlo manual con otro script.  
* Todos los comandos se ejecutan con permisos de admin.   

### Instrucciones:   

### Citado lo que debe ir en Powershell  
* Clonar el repositorio: **git clone https://github.com/96danielbaez/HyperV**  

* O sino descargalo desde **Google Drive** desde acá: [Script Hyper V](https://drive.google.com/file/d/1KyrJjDTal2zqMyHe7r0jFtiqa8XWiM-k/view?usp=drive_link)  

* Obtener el nombre de la GPU, y guardarlo para usarlo más adelante: **.\PreChecks.ps1**  
![Obteniendo nombre de GPU](https://github.com/96danielbaez/HyperV/blob/main/User/imagenes/guardar%20nombre%20gpu.png)    

* Para evitar cualquier problema con el script: **Set-ExecutionPolicy unrestricted**   
![Imagen ejecutando el script](https://github.com/96danielbaez/HyperV/blob/main/User/imagenes/politica.png)   

* Organizar las carpetas para luego copiar el path (ejemplo).   
![Imagen de ejemplo](https://github.com/96danielbaez/HyperV/blob/main/User/imagenes/ejemplo%20carpetas.png)   

* Ejecutar, editar los valores (path de la iso, path de úbicacion de disco virtual, cantidad de ram, nucleos, etc) y luego guardar : **notepad CopyFilesToVM.ps1**  
![Editar script con los parametros de la virtual](https://github.com/96danielbaez/HyperV/blob/main/User/imagenes/notepad.png)   

* Ya se puede ejecutar el script para que empiece el proceso de creación y seteo: **.\CopyFilesToVM.ps1**.  
![Copiando archivos](https://github.com/96danielbaez/HyperV/blob/main/User/imagenes/copiar%20archivos.png)   

* Luego finalizado, en la virtual descargar **Microsoft Visual C++ All in one** para poder ejecutar MU.  
https://www.techpowerup.com/download/visual-c-redistributable-runtime-package-all-in-one/   

* Listo papu, muleando xD
![Muleando a tope](https://github.com/96danielbaez/HyperV/blob/main/User/imagenes/muleando.png)  

# 💥 Actualizar gráfica en la virtual, luego de una actualización en la PC.
Es importante actualizar los controladores de la GPU de la máquina virtual después de haber actualizado los controladores de la GPU del host.
* Reiniciar la PC luego de actualizar los drivers en el host.  
* Ir a la ubicación donde tenemos los archivos del script y abrimos el powershell en esa ubicación o ubicarse allí con "cd".  
* Ejecutar: **Update-VMGpuPartitionDriver.ps1 -VMName "Nombre de la virtual" -GPUName "Nombre de la GPU"**.  
**AUTO** para W10, o el nombre de tu GPU que suelta el otro script, por ejemplo **NVIDIA GeForce RTX 2060**.  

# 🤔 Valores de CopyFilesToVM:  
  ```VMName = "VM1"``` - Nombre de la virtual  
  ```SourcePath = "C:\Users\Besta\Downloads\Win11_English_x64.iso"``` - Path de ISO de Windows  
  ```Edition    = 6``` - Dejalo como 6, esto significa windows 10 / 11 pro  
  ```VhdFormat  = "VHDX"``` - No tocar   
  ```DiskLayout = "UEFI"``` - No tocar    
  ```SizeBytes  = 30gb``` - 25-30 GB aprox  
  ```MemoryAmount = 4GB``` - Cantidad de RAM   
  ```CPUCores = 2``` - Cantidad de nucleos  
  ```NetworkSwitch = "Default Switch"``` - No tocar  
  ```VHDPath = "C:\Users\Public\Documents\Hyper-V\Virtual Hard Disks\"``` - Path del disco virtual.   
  ```UnattendPath = "$PSScriptRoot"+"\autounattend.xml"``` - No tocar   
  ```GPUName = "AUTO"``` - Nombre GPU o AUTO (W10)  
  ```GPUResourceAllocationPercentage = 50``` - Porcentaje de GPU  
  ```Username = "Virtual1"``` - Usuario     
  ```Password = "Virtual1"``` - Password  
  ```Autologon = "true"```- Iniciar automaticamente  

