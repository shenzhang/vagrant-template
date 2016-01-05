# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  ["1", "2", "3"].each do |n|
    config.vm.define "node#{n}" do |node_config|
      node_config.vm.box = "ubuntu/trusty64"
  
      node_config.vm.provision "ansible" do |ansible|
        ansible.playbook = "provision/ansible-playbook.yml"
        # ansible.limit = 'all'
        ansible.extra_vars = {
          id: "#{n}"
        }
      end

      node_config.vm.network "private_network", ip: "192.168.3.10#{n}"

      node_config.vm.provider :virtualbox do |vb|
        vb.name = "node#{n}"
        vb.cpus = 2
        vb.memory = 768
      end
    end
  end
  
end
