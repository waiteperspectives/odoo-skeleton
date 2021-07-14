# -*- mode: ruby -*-
# vi: set ft=ruby :
#

Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/bionic64"
  config.vm.network "forwarded_port", guest: 14069, host: 14069      # REQUIRED: http port
  config.vm.network "forwarded_port", guest: 14072, host: 14072      # REQUIRED: longpolling port
  config.vm.network "forwarded_port", guest: 5432, host: 14432       # postgres port - for using db admin tools
  # config.vm.network "forwarded_port", guest: 8025, host: 14025     # mailhog port https://github.com/mailhog/MailHog
  # config.disksize.size = "10GB"                                    # manage disksize using https://github.com/sprotheroe/vagrant-disksize
  config.vm.synced_folder "src/", "/home/vagrant/src"                # share src between host and guest

  config.vm.provider "virtualbox" do |vb|
    vb.memory = "2048"
    vb.cpus = "2"
    vb.name = "tmp-odoo"                                             # REQUIRED: name your box
  end

  config.vm.provision :shell, :inline => "sudo rm /etc/localtime && sudo ln -s /usr/share/zoneinfo/America/New_York /etc/localtime", run: "always"

  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "provisioning/playbooks/setup_postgres.yaml"
  end

  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "provisioning/playbooks/setup_odoo.yaml"
  end

  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "provisioning/playbooks/setup_node.yaml"
  end

  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "provisioning/playbooks/setup_vim.yaml"
  end

end
