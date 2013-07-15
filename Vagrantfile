# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure('2') do |config|
  config.vm.box = 'precise64'
  config.vm.box_url = 'http://files.vagrantup.com/precise64.box'
  config.vm.network :forwarded_port, guest: 3000, host: 3000

  config.vm.define :marozi, :facter => { "osfamily" => "centos" } do |marozi|
    marozi.vm.hostname = 'marozi.vagrant.localdomain'
    marozi.vm.network :private_network, ip: '10.0.0.10'

    marozi.vm.provision :puppet do |puppet|
      puppet.manifests_path = 'puppet/manifests'
      puppet.manifest_file  = 'marozi.pp'
      puppet.module_path    = 'puppet/modules'
    end
  end
end