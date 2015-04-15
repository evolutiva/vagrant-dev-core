# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

  config.vm.box = "chef/ubuntu-14.04"
  config.vm.hostname = "evolutiva-devel"
  # config.vm.box_check_update = false

  # Network
  config.vm.network "forwarded_port", guest: 80, host: 8080     #NginX
  config.vm.network "forwarded_port", guest: 9000, host: 9000   #Node 
  config.vm.network "forwarded_port", guest: 27017, host: 27017 #MongoDB
  config.vm.network "forwarded_port", guest: 3000, host: 3000   #Grunt
  config.vm.network "forwarded_port", guest: 8000, host: 8000   #Django 

  # using a specific IP.
  # config.vm.network "private_network", ip: "192.168.33.10"

  # Sync Folders
  # Change /path/to/working/dir
  config.vm.synced_folder "/path/to/working/dir", "/home/vagrant/html", id:"vagrant-www", owner:"vagrant", group:"vagrant", mount_options:["dmode=777,fmode=777"]
  # Install puppet for provisioning 
  config.vm.provision "shell", :inline => <<-SHELL
    sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv 7F0CEB10
    echo 'deb http://downloads-distro.mongodb.org/repo/ubuntu-upstart dist 10gen' | sudo tee /etc/apt/sources.list.d/mongodb.list

    sudo apt-get update
    #Install Optional
    sudo apt-get install -y nginx mongodb-org
    #Install DB
    sudo apt-get install -y postgresql-9.3
    #Install devel core
    sudo apt-get install -y python-pip build-essential vim zsh tmux curl git libc6-dev python-dev libpq-dev libcurl4-openssl-dev
    #Install images requirements
    sudo apt-get install -y python-imaging  python-dev libjpeg8 libjpeg8-dev libfreetype6 libfreetype6-dev
    #Install Python 3
    sudo apt-get install -y python3 python3-dev python3-software-properties python-virtualenv
    #Install Scrapy Requerimients
    sudo apt-get install libxml2-dev libxslt1-dev libssl-dev libffi-dev
    #Install Odoo Requerimients
    sudo apt-get install -y python-ldap libsasl2-dev
    cd;
    wget http://nodejs.org/dist/v0.10.32/node-v0.10.32.tar.gz
    tar xzf node-v0.10.32.tar.gz;
    cd node-v0.10.32;
    ./configure
    make
    sudo make install
    cd;
    sudo sed -i 's/\/usr\/share\/nginx\/html/\/home\/vagrant\/html/g' /etc/nginx/sites-available/default;
    sudo service nginx reload;

    curl -L http://install.ohmyz.sh | sh ;
    curl http://j.mp/spf13-vim3 -L -o - | sh ;

    echo "\033[0;32m"'                  _       _   _                              '"\033[0m"
    echo "\033[0;32m"'                 | |     | | (_)                             '"\033[0m"
    echo "\033[0;32m"'   _____   _____ | |_   _| |_ ___   ____ _   _ __ ___ __  __ '"\033[0m"
    echo "\033[0;32m"'  / _ \ \ / / _ \| | | | | __| \ \ / / _` | | |_ ` _ \\ \/ / '"\033[0m"
    echo "\033[0;32m"' |  __/\ V / (_) | | |_| | |_| |\ V / (_| |_| | | | | |>  <  '"\033[0m"
    echo "\033[0;32m"'  \___| \_/ \___/|_|\__,_|\__|_| \_/ \__,_(_)_| |_| |_/_/\_\ '"\033[0m"
    echo "\033[0;32m"'                                                             '"\033[0m"
    echo "\n\n \033[0;32mEntender, Crear, Comunicar.\033[0m"

  SHELL
end
