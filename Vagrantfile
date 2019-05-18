# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  os = "bento/ubuntu-18.04"
  net_ip = "192.168.50"
  role = "crab"

  config.vm.define role, primary: true do |master_config|
    master_config.vm.host_name = "#{role}.devops"
    master_config.vm.network "private_network", ip: "#{net_ip}.10"
    master_config.vm.box = "#{os}"
    master_config.vm.provider "virtualbox" do |vb|
      vb.memory = "1024"
      vb.cpus = 1
      vb.name = "#{role}"
    end
    #Mount folders
    #master_config.vm.synced_folder "../../GitRepos/", "/repos"
    
    # Ansible
    config.vm.provision "ansible_local" do |ansible|
      ansible.become = true
      ansible.playbook = "docker.yml"
    end
  end

end
