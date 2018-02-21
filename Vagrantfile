Vagrant.configure("2") do |config|
  config.vm.box = "centos/7"

  config.vm.define "tower" do |tower_config|
    tower_config.vm.network :private_network, ip: "192.168.1.100"
    tower_config.vm.provider "vmware_fusion" do |v|
      v.vmx["memsize"] = "4096"
      v.vmx["numvcpus"] = "4"
    end
    tower_config.vm.provision "ansible" do |ansible|
      ansible.playbook = "playbook.yml"
    end
  end

  config.vm.define "host1" do |host1_config|
    host1_config.vm.network :private_network, ip: "192.168.1.101"
  end

  config.vm.define "host2" do |host2_config|
    host2_config.vm.network :private_network, ip: "192.168.1.102"
  end

end
