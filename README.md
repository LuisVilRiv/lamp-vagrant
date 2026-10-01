# MV LAMP con Vagrant

Entorno LAMP (Apache, MariaDB, PHP) sobre `debian/bookworm64` con VirtualBox.

## Requisitos
- VirtualBox 7.x
- Vagrant 2.4.1 o superior (con VirtualBox 7.1 hace falta 2.4.1+; con la 7.2, 2.4.9+)
- Git
- Virtualización (VT-x/AMD-V) activada en la BIOS/UEFI

## Uso
    git clone https://github.com/LuisVilRiv/lamp-vagrant.git
    cd lamp-vagrant
    vagrant up

Abrir http://localhost:8080/info.php

## Aprovisionamiento selectivo
    vagrant rsync
    vagrant provision --provision-with install_packages
    vagrant provision --provision-with configure_lamp

## Notas por sistema
- **Ubuntu/Debian:** instalar VirtualBox y Vagrant desde sus repositorios oficiales (los de la distro suelen ser antiguos).
- **Windows:** usar PowerShell o Git Bash. Si Hyper-V o WSL2 están activos, VirtualBox puede ir lento o fallar.
- **macOS:** en Mac con chip Apple (ARM) la caja `debian/bookworm64` no funciona con VirtualBox.
- **Fedora:** instalar `kernel-devel` del kernel en uso y ejecutar `sudo /sbin/vboxconfig`.

## Problemas conocidos
- Puerto 8080 ocupado: cambiar `host: 8080` en el Vagrantfile.
- `/vagrant` vacío: ejecutar `vagrant rsync`.
