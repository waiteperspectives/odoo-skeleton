# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/bionic64"
  config.vm.network "forwarded_port", guest: 14069, host: 14069
  config.vm.network "forwarded_port", guest: 8025, host: 14025

  config.vm.provider "virtualbox" do |vb|
    vb.memory = "2048"
    vb.cpus = "2"
    vb.name = "tmp-odoo"
  end

  # Set the timezone to the host timezone
  config.vm.provision :shell, :inline => "sudo rm /etc/localtime && sudo ln -s /usr/share/zoneinfo/America/New_York /etc/localtime", run: "always"

  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "playbook.yaml"
  end
end