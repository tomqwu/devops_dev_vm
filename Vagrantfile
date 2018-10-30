Vagrant.configure("2") do |config|
  config.vm.provider "virtualbox" do |v|
    v.memory = 4096
    v.cpus = 4
    v.name = "devops_vm"
  end

  config.vm.box = "bento/ubuntu-18.04"

  config.vm.network "public_network"
  
  config.vm.network "forwarded_port", guest: 52698, host: 52698 # rmate
  config.vm.network "forwarded_port", guest: 8080, host: 8080
  config.vm.network "forwarded_port", guest: 4403, host: 4403
  config.vm.network "forwarded_port", guest: 9876, host: 9876
  for i in 32768..32800
    config.vm.network "forwarded_port", guest: i, host: i
  end

  config.vm.provision "ansible_local" do |ansible|
    ansible.playbook = "ansible-install.yml"
    #ansible.verbose  = true
    ansible.become   = true
  end
end
