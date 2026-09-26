

### Requisitos: 
* Última versión de Windows 10 ISO [Descargar Aquí](https://www.microsoft.com/en-gb/software-download/windows10ISO) / Windows 11 ISO [Descargar Aquí](https://www.microsoft.com/en-us/software-download/windows11) - 
* Virtualización activada en BIOS Y [Hyper-V activado](https://docs.microsoft.com/en-us/virtualization/hyper-v-on-windows/quick-start/enable-hyper-v) en Windows 10/ 11. (requiere reiniciar).  
* Todos los scripts se ejecutan en Powershell con permisos de admin. 

### Instrucciones:
1. Descargar el repo o conseguir los archivos.
2. Ejecutar en powershell -> "PreChecks.ps1" para obtener el nombre de la GPU, guardarlo.
4. Ejecutar en powershell -> "Set-ExecutionPolicy unrestricted".
3. Ejecutar en powershell -> "notepad CopyFilesToVM.ps1" y editar valores (path de la iso, path de úbicacion de disco virtual, cantidad de ram, nucleos, etc).
4. Ejecutar en powershell -> "CopyFilesToVM.ps1".
5. Luego en la pc descargar Microsoft Visual C++ All in one para poder ejecutar MU.

### Actualizar gráfica en la virtual, luego de que se actualiza en el host (cuando se corrompe):
Es importante actualizar los controladores de la GPU de la máquina virtual después de haber actualizado los controladores de la GPU del host.
1. Reiniciar la PC luego de actualizar los drivers en el host.  
2. Ir a la ubicación donde tenemos los archivos del script y abrimos el powershell en esa ubicación o ubicarse allí con "cd".
3. Ejecutar ```Update-VMGpuPartitionDriver.ps1 -VMName "Nombre de la virtual" -GPUName "Nombre de la GPU"```. (AUTO en w10)

### Valores
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
  ```Username = "Virtual1"``` - Usuario dentro de la virtual  
  ```Password = "VM1"``` - Password VM1
  ```Autologon = "true"```- Iniciar automaticamente

