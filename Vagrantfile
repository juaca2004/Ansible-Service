# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|

  # --- Servidor Principal ---
  config.vm.define "serverPrincipal" do |serverPrincipal|
    serverPrincipal.vm.box = "ubuntu/jammy64"
    serverPrincipal.vm.hostname = "serverPrincipal"
	  serverPrincipal.vm.network "public_network", ip: "192.168.1.200", bridge: "Realtek 8821CE Wireless LAN 802.11ac PCI-E NIC"
    serverPrincipal.vm.provider "virtualbox" do |vb|
      vb.customize ["modifyvm", :id, "--memory", "512", "--cpus", "1", "--name", "serverPrincipal"]
    end
    serverPrincipal.vm.provision "shell", inline: <<-SHELL
      sudo apt update
      sudo apt install python3-pip -y
      pip3 install PyMySQL
    SHELL
  end

  # --- Servidor Secundario ---
  config.vm.define "serverSecundario" do |serverSecundario|
    serverSecundario.vm.box = "ubuntu/jammy64"
    serverSecundario.vm.hostname = "serverSecundario"
    serverSecundario.vm.network "public_network", ip: "192.168.1.201", bridge: "Realtek 8821CE Wireless LAN 802.11ac PCI-E NIC"
    serverSecundario.vm.provider "virtualbox" do |vb|
      vb.customize ["modifyvm", :id, "--memory", "512", "--cpus", "1", "--name", "serverSecundario"]
    end
    serverSecundario.vm.provision "shell", inline: <<-SHELL
      sudo apt update
      sudo apt install python3-pip -y
      pip3 install PyMySQL
    SHELL
  end

  # --- Webserver ---
  config.vm.define "webserver" do |webserver|
    webserver.vm.box = "ubuntu/jammy64"
    webserver.vm.hostname = "webserver"
    webserver.vm.network "public_network", ip: "192.168.1.202", bridge: "Realtek 8821CE Wireless LAN 802.11ac PCI-E NIC"
    webserver.vm.provider "virtualbox" do |vb|
      vb.customize ["modifyvm", :id, "--memory", "512", "--cpus", "1", "--name", "webserver"]
    end
    webserver.vm.provision "shell", inline: <<-SHELL
      sudo apt update
      sudo apt install python3-pip -y
      pip3 install PyMySQL
    SHELL
  end
end
