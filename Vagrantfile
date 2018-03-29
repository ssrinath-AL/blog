# -*- mode: ruby -*-
# vi: set ft=ruby :
# See https://github.com/discourse/discourse/blob/master/docs/VAGRANT.md
#
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box= "ubuntu/trusty64"

  config.vm.network :private_network, ip: "192.168.33.48"  
  
  config.vm.provider :virtualbox do |v|
    v.customize ["modifyvm", :id, "--memory", "512"]
    v.customize ["modifyvm", :id, "--cpus", "1"]
    v.customize ["modifyvm", :id, "--natdnsproxy1", "on"]
    v.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
    v.customize ["modifyvm", :id, "--nictype1", "virtio"]
  end

  config.vm.synced_folder ".", "/home/vagrant/blog",
    mount_options: ["dmode=775,fmode=664"]

  config.vm.provision "shell",
    inline: "sudo apt-get update"
  config.vm.provision "shell",
    inline: "sudo apt-get -y install python3-pip"
  config.vm.provision "shell",
    inline: "sudo pip3 install --upgrade setuptools pip && sudo pip3 install --upgrade 'Nikola[extras]' "

  config.vm.provision "shell",
    inline: "apt-get install -y tofrodos wget zip" 
  
end
