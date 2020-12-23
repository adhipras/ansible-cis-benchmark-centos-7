# -*- mode: ruby -*-
# vi: set ft=ruby :

# A workaround solution to resolve DHCP with private network failure issue on VirtualBox.
# Reference: https://github.com/hashicorp/vagrant/issues/8878
class VagrantPlugins::ProviderVirtualBox::Action::Network
  def dhcp_server_matches_config?(dhcp_server, config)
    true
  end
end

# All Vagrant configuration is done below.
# The "2" in Vagrant.configure configures the configuration version
# (we support older styles for backwards compatibility).
# Please don't change it unless you know what you're doing.
Vagrant.configure("2") do |config|

  # Every Vagrant development environment requires a box.
  # You can search for boxes at https://vagrantcloud.com/search.
  config.vm.box = "centos/7"

  # Disable automatic VirtualBox Guest Additions version checking
  # VirtualBox Guest Additions ISO file downloading
  # when booting this machine.
  if Vagrant.has_plugin?("vagrant-vbguest")
    config.vbguest.auto_update = false
    config.vbguest.no_remote = true
  end

  # Define the VM.
  config.vm.define "centos"

  # Create a private network, which allows host-only access to the machine
  # using an IP address from the reserved address space assigned via DHCP.
  config.vm.network "private_network", type: "dhcp"

  # VirtualBox specific configurations.
  config.vm.provider "virtualbox" do |vb|
    vb.cpus = 1
    vb.memory = 1024
    vb.name = "CentOS-7"
    vb.customize ["modifyvm", :id, "--cpuexecutioncap", 100]
  end

  # Enable provisioning with Ansible playbook.
  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "playbook.yml"
    ansible.groups = {
      "virtualbox" => ["centos"]
    }
  end
end
