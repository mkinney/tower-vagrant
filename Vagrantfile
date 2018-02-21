Vagrant.configure("2") do |config|
  config.vm.box = "centos/7"

  config.vm.network :private_network, ip: "192.168.1.100"

  config.vm.provider "vmware_fusion" do |v|
    v.vmx["memsize"] = "4096"
    v.vmx["numvcpus"] = "4"
  end

  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "playbook.yml"
  end

end
