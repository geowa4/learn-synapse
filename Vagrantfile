# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.provider "virtualbox" do |vb, override|
    override.vm.box = "box-cutter/fedora20"
  end

  config.vm.define "test" do |api|
    api.vm.network "private_network", ip: "192.168.50.8"
  end

  config.vm.provision "ansible", run: "always" do |ansible|
    ansible.groups = {
      "test"    => ["test"],
    }
    ansible.playbook = "deploy/vagrant.yml"
  end
end
