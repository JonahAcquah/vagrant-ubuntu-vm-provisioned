# -*- mode: ruby -*-
# vim: set ft=ruby :

VAGRANTFILE_API_VERSION = '2'

hostname = 'ubuntu'
ip_address = '10.10.10.33'
Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

  config.vm.box = "boxcutter/ubuntu1604-desktop"
  config.vm.box_check_update = false
  config.vm.network :private_network, ip:ip_address

  config.vm.provider "virtualbox" do |v|
    v.gui = true
    v.memory = 3072
    v.cpus = 2
    v.name = hostname
  end
  
  config.vm.provision :ansible_local do |ansible|
    ansible.verbose        = "v"
    ansible.playbook       = "playbook.yml"
	ansible.limit          = hostname
    ansible.inventory_path = "host.yml"
  end
  
end