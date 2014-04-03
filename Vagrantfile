# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"
BASE_IP = "192.168.56.10"
MASTER_IP = "192.168.56.20"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

  config.vm.box = "debian-73-x64-virtualbox-puppet"
  config.vm.box_url = "http://puppet-vagrant-boxes.puppetlabs.com/debian-73-x64-virtualbox-puppet.box"
  
  (0..3).each do |i|
    config.vm.define "galera00#{i}" do |galera|
      galera.vm.network :private_network, ip: "#{BASE_IP}#{i}"
      galera.vm.hostname = "galera00#{i}.olindata.vm"
      galera.vm.provision "shell",
        inline: "echo #{MASTER_IP} master.olindata.vm master puppet >> /etc/hosts"
      galera.vm.provision "shell",
        inline: "echo nameserver 8.8.8.8 > /etc/resolv.conf"
    end
  end
end
