Vagrant.configure(2) do |config|  
  config.vm.define "dhcp" do |dhcp|
    dhcp.vm.box = "ubuntu/trusty64"
    dhcp.vm.hostname = "dhcp"
    dhcp.vm.network "private_network", ip:"10.10.20.4" 
    dhcp.vm.provider "virtualbox" do |vb|
      vb.memory = "1024"  
    end 
    dhcp.vm.provision "shell", inline: <<-SHELL
        sudo apt-get update

        # DHCP Server installieren
        sudo apt-get -y install isc-dhcp-server

	# Firewall aktivieren
        sudo apt-get -y install ufw gufw 
        sudo ufw allow from 10.0.2.2 to any port 22
        sudo ufw --force enable    
SHELL
    end  
 end