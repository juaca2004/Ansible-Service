# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|

  # --- Servidor Principal ---
  config.vm.define "serverPrincipal" do |serverPrincipal|
    serverPrincipal.vm.box = "ubuntu/jammy64"
    serverPrincipal.vm.hostname = "serverPrincipal"
    serverPrincipal.vm.network "public_network", ip: "192.168.88.170"
    serverPrincipal.vm.network "private_network", ip: "192.168.57.10"
    # serverPrincipal.vm.network "private_network", ip: "2001:db8:1::100", bridge: "Realtek 8821CE Wireless LAN 802.11ac PCI-E NIC"
    serverPrincipal.vm.provider "virtualbox" do |vb|
      vb.customize ["modifyvm", :id, "--memory", "512", "--cpus", "1", "--name", "serverPrincipal"]
    end
    serverPrincipal.vm.provision "shell", inline: <<-SHELL
      sudo apt update
      sudo apt install python3-pip -y
      pip3 install PyMySQL
      
      NETPLAN_FILE="/etc/netplan/01-netcfg.yaml"
      sudo bash -c "cat > $NETPLAN_FILE" << EOF
network:
  version: 2
  renderer: networkd
  ethernets:
    enp0s8:
      addresses:
      - 192.168.88.170/24
      - 2001:db8:1::100/64
EOF
      sudo netplan apply
    SHELL
end

  # --- Servidor Secundario ---
  config.vm.define "serverSecundario" do |serverSecundario|
    serverSecundario.vm.box = "ubuntu/jammy64"
    serverSecundario.vm.hostname = "serverSecundario"
    serverSecundario.vm.network "public_network", ip: "192.168.88.171"
    serverSecundario.vm.network "private_network", ip: "192.168.57.11"
    serverSecundario.vm.provider "virtualbox" do |vb|
      vb.customize ["modifyvm", :id, "--memory", "512", "--cpus", "1", "--name", "serverSecundario"]
    end
    serverSecundario.vm.provision "shell", inline: <<-SHELL
      sudo apt update
      sudo apt install python3-pip -y
      pip3 install PyMySQL
      
      NETPLAN_FILE="/etc/netplan/01-netcfg.yaml"
      sudo bash -c "cat > $NETPLAN_FILE" << EOF
network:
  version: 2
  renderer: networkd
  ethernets:
    enp0s8:
      addresses:
      - 192.168.88.171/24
      - 2001:db8:1::101/64
EOF
      sudo netplan apply
    SHELL
end

  # --- Webserver ---
  config.vm.define "webserver" do |webserver|
    webserver.vm.box = "ubuntu/jammy64"
    webserver.vm.hostname = "webserver"
    webserver.vm.network "public_network", ip: "192.168.88.202"
    webserver.vm.provider "virtualbox" do |vb|
      vb.customize ["modifyvm", :id, "--memory", "512", "--cpus", "1", "--name", "webserver"]
    end
    webserver.vm.provision "shell", inline: <<-SHELL
      sudo apt update
      sudo apt install python3-pip -y
      pip3 install PyMySQL
      sudo apt install nginx
    SHELL
  end
end
