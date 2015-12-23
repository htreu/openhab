# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = "ubuntu/trusty32"

  config.vm.network "public_network", ip: "192.168.0.99", bridge: "en0: Ethernet"

  if Vagrant.has_plugin?("vagrant-timezone")
    config.timezone.value = "Europe/Berlin"
  end

  # If true, then any SSH connections made will enable agent forwarding.
  # Default value: false
  # config.ssh.forward_agent = true

  config.vm.provider "virtualbox" do |vb|
        # set vm memory to 756MB
    vb.customize ["modifyvm", :id, "--memory", "756"]
        # set time resync to 1dd0 seconds:
        #vb.customize [ "guestproperty", "set", :id, "/VirtualBox/GuestAdd/VBoxService/--timesync-set-threshold", 10000 ]
  end

  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "ansible/playbook.yml"
  end
end
