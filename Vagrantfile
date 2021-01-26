# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.ssh.forward_agent = true
  config.vm.box = "ubuntu/bionic64"
  config.vm.hostname = "testing-tools"
  config.vm.network :public_network, bridge: ''
  config.vm.network "forwarded_port", guest: 3000, host: 3000
  config.vm.network "forwarded_port", guest: 80, host: 1234 
  config.vm.network "forwarded_port", guest: 8080, host: 8080
  config.vm.synced_folder "./", "/home/vagrant/shared"

  config.vm.provider :virtualbox do |vb|
    vb.name = "testing-tools"
    vb.memory = 2048
    vb.cpus = 1
    vb.linked_clone = true
  end

#  subconfig.vm.provision "shell"
#    subconfig.vm.provision "shell", inline: <<-SHELL
#    sudo apt -y update
#    sudo apt install -y software-properties-common
#    sudo apt-add-repository -y ppa:ansible/ansible
#    sudo apt -y update
#    sudo apt install -y ansible
#    SHELL
#  end

  config.vm.provision "ansible" do |ansible|
    ansible.config_file = "ansible.cfg"
    ansible.playbook = "playbook.yml"
  end

end

