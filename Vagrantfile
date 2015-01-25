# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = "ubuntu/trusty32"

  # config.vm.network "forwarded_port", guest: 80, host: 8080

  #config.vm.network "private_network", ip: "192.168.0.98"
  config.vm.network "public_network", ip: "192.168.0.99"

  if Vagrant.has_plugin?("vagrant-timezone")
    config.timezone.value = "Europe/Berlin"
  end

  # If true, then any SSH connections made will enable agent forwarding.
  # Default value: false
  # config.ssh.forward_agent = true

  config.vm.provider "virtualbox" do |vb|
        # set vm memory to 512MB
  	vb.customize ["modifyvm", :id, "--memory", "512"]
        # set time resync to 10 seconds:
        vb.customize [ "guestproperty", "set", :id, "/VirtualBox/GuestAdd/VBoxService/--timesync-set-threshold", 10000 ]
  end

  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "ansible/playbook.yml"
  end
end

