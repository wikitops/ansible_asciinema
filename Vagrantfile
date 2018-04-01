# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|

  config.vm.box = "ubuntu/xenial64"

  # Asciinema Server
  (1..1).each do |i|
    config.vm.provider "virtualbox" do |vb|
      vb.memory = 2048
      vb.cpus = 2
    end

    config.vm.define "asciinema-server0#{i}" do |server|
      server.vm.hostname = "asciinema-server0#{i}"
      server.vm.network "private_network", ip: "10.0.3.9#{i}"
    end
  end

  # Asciinema Recorder
  (1..1).each do |i|
    config.vm.provider "virtualbox" do |vb|
      vb.memory = 2048
      vb.cpus = 2
    end

    config.vm.define "asciinema-recorder0#{i}" do |server|
      server.vm.hostname = "asciinema-recorder0#{i}"
      server.vm.network "private_network", ip: "10.0.3.10#{i}"
    end
  end

  # Provision
  config.vm.provision "shell", path: "provision.sh"
  config.vm.provision "file", source: "~/.ssh/id_rsa.pub", destination: "/home/vagrant/.ssh/authorized_keys"

end
