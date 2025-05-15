# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.define "serverPrincipal" do |serverPrincipal|
  	serverPrincipal.vm.box = "ubuntu/jammy64"
  	serverPrincipal.vm.hostname = "serverPrincipal"
  	serverPrincipal.vm.network "public_network", ip:"192.168.88.170"
  	serverPrincipal.vm.network "private_network", ip: "192.168.57.10"
  	serverPrincipal.vm.provider "virtualbox" do |vb|
  		 vb.customize ["modifyvm", :id, "--memory", "512", "--cpus", "1", "--name", "serverPrincipal"]
  	end
  	serverPrincipal.vm.provision "shell", inline:
  	<<-SHELL
  	apt update
  	sudo apt install python3-pip -y
	pip3 install PyMySQL
  	SHELL
  end
    config.vm.define "serverSecundario" do |serverSecundario|
  	serverSecundario.vm.box = "ubuntu/jammy64"
  	serverSecundario.vm.hostname = "serverSecundario"
  	serverSecundario.vm.network "public_network", ip:"192.168.88.171"
  	serverSecundario.vm.network "private_network", ip: "192.168.57.11"
  	serverSecundario.vm.provider "virtualbox" do |vb|
  		vb.customize ["modifyvm", :id, "--memory", "512", "--cpus", "1", "--name", "serverSecundario"]
  	end
  	serverSecundario.vm.provision "shell", inline:
  	<<-SHELL
  	apt update
  	sudo apt install python3-pip -y
	pip3 install PyMySQL
  	SHELL
  end
end
