# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure("2") do |config|
  # The most common configuration options are documented and commented below.
  # For a complete reference, please see the online documentation at
  # https://docs.vagrantup.com.

  # Every Vagrant development environment requires a box. You can search for
  # boxes at https://vagrantcloud.com/search.
  config.vm.define "lb1" do |lb1|
    lb1.vm.box = "ubuntu/trusty64"
    lb1.vm.network "private_network", ip: "10.0.0.13"
    lb1.vm.provision "shell", path:"https://gist.githubusercontent.com/Stephen-Njoroge/5f00c664f6e826edb363dceb9a1cd9dc/raw/c5755ec284f163f1835b641b99d5a99c6ffd4e17/provision-lb.sh"
  end
  config.vm.define "web1" do |web1|
    web1.vm.box = "ubuntu/trusty64"
    web1.vm.network "private_network", ip: "10.0.0.14"
    web1.vm.provision :shell do |shell|
      shell.args = "1"
      shell.path = "https://gist.githubusercontent.com/Stephen-Njoroge/b170de71af586999802154b1cf426b72/raw/8e6f689fb6166e22ce3386ee2874e4ec9fa6bd3d/provision-web.sh"
    end
  end

  config.vm.define "web2" do |web2|
    web2.vm.box = "ubuntu/trusty64"
    web2.vm.network "private_network", ip: "10.0.0.15"
    web2.vm.provision :shell do |shell|
      shell.args = "2"
      shell.path = "https://gist.githubusercontent.com/Stephen-Njoroge/b170de71af586999802154b1cf426b72/raw/8e6f689fb6166e22ce3386ee2874e4ec9fa6bd3d/provision-web.sh"
    end
  end
  config.vm.define "my_db" do |my_db|
   my_db.vm.box = "ubuntu/trusty64"
   my_db.vm.network "forwarded_port", guest: 3306, host: 3306
   my_db.vm.network "private_network", ip: "10.0.0.16" 
   my_db.vm.provision :shell do |shell|
   shell.path = "https://gist.githubusercontent.com/Stephen-Njoroge/1c7d448b5aa6bb43d90aaa8c6358cb4b/raw/94271dda9751eb01ffe89e9d2d278176dba27f34/provision-db.sh"
 end
end

  # Disable automatic box update checking. If you disable this, then
  # boxes will only be checked for updates when the user runs
  # `vagrant box outdated`. This is not recommended.
  # config.vm.box_check_update = false

  # Create a forwarded port mapping which allows access to a specific port
  # within the machine from a port on the host machine. In the example below,
  # accessing "localhost:8080" will access port 80 on the guest machine.
  # NOTE: This will enable public access to the opened port
  # config.vm.network "forwarded_port", guest: 80, host: 8080

  # Create a forwarded port mapping which allows access to a specific port
  # within the machine from a port on the host machine and only allow access
  # via 127.0.0.1 to disable public access
  # config.vm.network "forwarded_port", guest: 80, host: 8080, host_ip: "127.0.0.1"

  # Create a private network, which allows host-only access to the machine
  # using a specific IP.
  # config.vm.network "private_network", ip: "192.168.33.10"

  # Create a public network, which generally matched to bridged network.
  # Bridged networks make the machine appear as another physical device on
  # your network.
  # config.vm.network "public_network"

  # Share an additional folder to the guest VM. The first argument is
  # the path on the host to the actual folder. The second argument is
  # the path on the guest to mount the folder. And the optional third
  # argument is a set of non-required options.
  # config.vm.synced_folder "../data", "/vagrant_data"

  # Provider-specific configuration so you can fine-tune various
  # backing providers for Vagrant. These expose provider-specific options.
  # Example for VirtualBox:
  #
  # config.vm.provider "virtualbox" do |vb|
  #   # Display the VirtualBox GUI when booting the machine
  #   vb.gui = true
  #
  #   # Customize the amount of memory on the VM:
  #   vb.memory = "1024"
  # end
  #
  # View the documentation for the provider you are using for more
  # information on available options.

  # Enable provisioning with a shell script. Additional provisioners such as
  # Puppet, Chef, Ansible, Salt, and Docker are also available. Please see the
  # documentation for more information about their specific syntax and use.
  # config.vm.provision "shell", inline: <<-SHELL
  #   apt-get update
  #   apt-get install -y apache2
  # SHELL
end
