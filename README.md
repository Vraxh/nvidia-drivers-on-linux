# nvidia-drivers-on-linux
Este repositorio es la documentacion de como instale los drivers privados nvidia en mi Arch y no perder en el progreso en el intento, los comandos, y las cosas que hago son diferentes en cada distro!

> [!WARNING]
> Drivers: Privados de la web oficial [NVIDIA](https://www.nvidia.com/es-la/drivers/) y Sistema Operativo: [Arch](https://wiki.archlinux.org/title/Main_page)

## 1. Antes de la instalación de los DRIVERS NVIDIA
> [!IMPORTANT]
> Haga una copia de seguridad de los archivos importantes antes de comenzar la instalación.
> Y esto es, por supuesto, bajo su propio riesgo, porque las tarjetas gráficas, los componentes y los monitores son diferentes y algunas combinaciones pueden causar resultados totalmente inesperados.

### 1.1 Desactive el arranque seguro de UEFI o comprobar cómo firmar el módulo del kernel de NVIDIA
#### La comprobación es UEFI Secure Boot Habilitado o Deshabilitado
- bootctl

System:


Firmware: n/a (n/a) 

Firmware Arch: x64

Secure Boot: disabled (setup)

TPM2 Support: yes

Measured UKI: no

Boot into FW: supported

## 2. Instalar drivers propietarios de NVIDIA y desactivar drivers nouveau
### 2.1 Descargar drivers NVIDIA
Ir a https://www.nvidia.com/es-la/drivers/ y descargar la ultima versión de los drivers, esta parte es diferente para todos, ya que depende de que grafica tengamos

>[!IMPORTANT]
>Hay que tener en cuenta que los drivers actualmente son compatible con el Kernel de Linux:	4.15 en adelante, si estas en LTS ya corre por tu cuenta, revisar los requisitos minimos del driver

### 2.2 Hacer ejecutable el instalador de NVIDIA
> En la ruto donde se encuentra el drivers, le damos persimo de ejecucion
 
- chmod +x /path/to/NVIDIA-Linux-*.run
  
### 2.3 Cambiamos a usuario root
-  su -
  
O

- sudo -i

### 2.4 Comprobar que el sistema este actualizado
#### 2.4.1 Actualiza completamente tu sistema
- pacman -Syu

#### 2.4.2 Después de la actualización, reiniciar:
- reboot

### 2.5 Instalar las dependencias necesarias

- sudo pacman -S linux-headers gcc make dkms acpid libglvnd pkgconf libxcb egl-wayland base basa-devel

### 2.6 Desactivar nouveau
- echo "blacklist nouveau" >> /etc/modprobe.d/blacklist.conf

### 2.7 Configurar parámetros del kernel
Abrir el archivo que se encuentra

- sudo nvim /etc/default/grub

y en la linea GRUB_CMDLINE_LINUX_DEFAULT dentro de las comillas poner los siguientes parametros nvidia_drm.modeset=1 nvidia_drm.fbdev=0

Guarda el archivo y regenerar la configuración de GRUB:
- sudo grub-mkconfig -o /boot/grub/grub.cfg

### 2.8 Desactivar entorno grafico para la instalación y reinicar 
- sudo systemctl set-default multi-user.target
- reboot
## 2.9 Instalar controladores propietarios de NVIDIA
### 2.9.1 Iniciar sesión como usuario root
-  su -
  
O

- sudo -i

### 2.9.2 Ejecutar NVIDIA
- ./NVIDIA-Linux-*.run

### 2.9.3 Activar entorno grafico y reiniciar
- sudo systemctl set-default graphical.target
-reboot
