Vagrant::Config.run do |config|

  config.vm.define :web do |web_config|
    web_config.vm.box = "precise64_base"
    web_config.vm.box_url = "http://files.vagrantup.com/precise64_vmware.box"
    web_config.vm.forward_port 80, 8080
    web_config.vm.network :bridged
    web_config.vm.network :hostonly, "192.168.100.10"

    web_config.vm.provision :ansible do |ansible|
      ansible.playbook = "ops/vagrant.yml"
	  ansible.inventory_file = "ops/vagrant-hosts"
    end
  end

  config.vm.define :db do |db_config|
    db_config.vm.box = "precise64_base"
    db_config.vm.box_url = "http://files.vagrantup.com/precise64_vmware.box"
    db_config.vm.forward_port 5432, 54322
    db_config.vm.network :bridged
    db_config.vm.network :hostonly, "192.168.100.20"

    db_config.vm.provision :ansible do |ansible|
      ansible.playbook = "ops/dbserver.yml"
	  ansible.inventory_file = "ops/vagrant-hosts"
    end
  end

end