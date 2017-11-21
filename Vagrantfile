# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure("2") do |config|
  config.vm.define "devops-appserver"
  config.vm.define "first"
  config.vm.define "second"
  # The most common configuration options are documented and commented below.
  # For a complete reference, please see the online documentation at
  # https://docs.vagrantup.com.

  # Every Vagrant development environment requires a box. You can search for
  # boxes at https://vagrantcloud.com/search.

config.vm.define "devops-appserver" do |devops-appserver|

  config.vm.box = "devops-appserver"
  config.vm.network "forwarded_port", guest: 80, host: 8080
  config.vm.synced_folder "../../devops-kungfu", "/home/vagrant/devops-kungfu", create: true
  
end

config.vm.define "first" do |first|

  first.vm.box = "centos/7"
  first.vm.base_mac = "246824682468"
  first.vm.network "private_network", ip: "19.91.8.12"
  first.vm.network "forwarded_port", guest: 80, host: 80,
        auto_correct: true

    # Define the provision file.
  #first.vm.provision :shell, :path => "web-bootstrap.sh"
  #first.vm.provision "shell", path: "web-bootstrap.sh"
    # Define a folder to map for locally hosted RPM files.
    # This is where we'll get the Oracle Instant Client files from.
    #web.vm.synced_folder "~/Vagrant/packages", "/opt/packages"
  #first.vm.synced_folder "~/VirtualBox\ VMs/VagrantFILE/packages", "/opt/packages"


    # Define a location for your local checkout of your webapp.
    #web.vm.synced_folder "~/Source/webapp", "/local/www/webapp"
  #first.vm.synced_folder "~/VirtualBox\ VMs/VagrantFILE/webapp", "/local/www/webapp"

end


config.vm.define "second" do |second|

  second.vm.box = "ubuntu/trusty64"
  second.vm.base_mac = "a2b2c2d8e9f1"
  second.vm.network "private_network", ip: "19.91.8.13"
  second.vm.network "forwarded_port", guest: 80, host: 80,
        auto_correct: true

second.vm.provision "shell", inline: <<-SHELL
    apt-get update
    apt-get install -y apache2
   SHELL
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
