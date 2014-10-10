Evolutiva.mx Vagrant Devel Core
=========

Levanta una maquina virtual con Ubuntu 14.04 ([chef/ubuntu_14.04]) e instala los siguientes paquetes: 

  - Node.js
  - MongoDB
  - VIM
  - Tmux
  - zsh & oh my Zsh!
  - NginX
  - spf13
  - python pip

El entorno base debe terminar de configurarse dejando a ZSH como shell por defecto, para ello se ejecuta:

```sh
chsh -s `which zsh` # passwd: vagrant
```
Instalación
-----------
Se debe el path de archivos sincronizados por el que se requiera usar con el fin de tener acceso a estos archivos desde la maquina virtual

```sh
# cambiar por la carpeta de acceso, esta carpeta estará disponible como default path de nginx y se montara en la maquina virtual en el siguiente punto:  /home/vagrant/html
24: config.vm.synced_folder "/home/sachiel/cod3", "/home/vagrant/html", id:"vagrant-www"
```

Base de Datos Relacional
-----------

Ningun motor de base de datos está instalado por defecto, a continuación algunos links de interes al respecto

* [PostgreSQL] - Motor de Base de Datos recomendado
* [MariaDB] - Alternativa a MySQL

Version
----

0.1

License
----

[GNU GPL v3]


**Free Software, Yeah!, [evolutiva.mx] rulz!**
[MariaDB]:https://downloads.mariadb.org/mariadb/repositories/#mirror=syringa&distro=Ubuntu&distro_release=trusty&version=10.1
[PostgreSQL]:http://technobytz.com/install-postgresql-9-3-ubuntu.html
[GNU GPL v3]:http://www.gnu.org/licenses/gpl.html
[evolutiva.mx]:http://evolutiva.mx
[chef/ubuntu_14.04]:https://vagrantcloud.com/chef/boxes/ubuntu-14.04
