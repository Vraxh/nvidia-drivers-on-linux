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
[vraxh@archlinux ~]$ bootctl

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
