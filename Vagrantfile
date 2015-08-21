# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = "debian/jessie64"
  config.vm.network "private_network", ip: "10.10.10.10"

  config.vm.synced_folder "../puppet", "/opt/opensource.org/puppet"

  config.vm.provision "puppet" do |puppet|
    puppet.manifests_path = "../puppet/manifests"
    puppet.manifest_file  = "site.pp"
    puppet.module_path = "../puppet/modules"
    puppet.hiera_config_path = "../puppet/hieradata"

    puppet.working_directory = '/opt/opensource.org/puppet'

    puppet.options = ['--parser=future']
  end
end
