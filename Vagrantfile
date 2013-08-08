Vagrant.configure("2") do |config|
 config.vm.synced_folder "/", "/vagrant", disabled: true

 config.vm.define :vpn do |vpn_config|
    vpn_config.vm.box = "precise64"
    vpn_config.vm.hostname = "vpn"
    vpn_config.vm.network :private_network, ip: "192.168.50.2"
    vpn_config.vm.network :forwarded_port, guest: 22, host: 2200, id: "ssh", auto_correct: true
  
    vpn_config.vm.provision :ansible do |ansible|
      ansible.playbook = "vpnservers.yml"
      ansible.inventory_file = "hosts-vagrant"
      ansible.verbose = true
    end
  end

end