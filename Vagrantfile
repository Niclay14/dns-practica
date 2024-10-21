# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "debian/bookworm64"
  config.vm.provision "shell", inline: <<-SHELL
  apt-get update
  apt-get install -y bind9 bind9-dnsutils
SHELL

  config.vm.define "tierra" do |tierra|
    tierra.vm.network "private_network", ip: "192.168.57.103"
    tierra.vm.hostname = "tierra.sistema.test"  
    tierra.vm.provision "shell", name: "master-dns", inline: <<-SHELL
      cp -v /vagrant/named.conf.options /etc/bind/
      cp -v /vagrant/named /etc/default/
      cp -v /vagrant/tierra/named.conf.local /etc/bind/
      cp -v /vagrant/db.sistema.test.rev /var/lib/bind/
      cp -v /vagrant/db.sistema.test.dns /var/lib/bind/
      chown :bind /var/lib/bind/*
      systemctl restart named
    SHELL

  end
   

  config.vm.define "venus" do |venus|
    venus.vm.network "private_network", ip: "192.168.57.102"
    venus.vm.hostname = "venus.sistema.test"
    venus.vm.provision "shell", name: "slave-dns", inline: <<-SHELL
      cp -v /vagrant/named /etc/default/
      cp -v /vagrant/named.conf.options /etc/bind/
      cp -v /vagrant/venus/named.conf.local /etc/bind/
      
      systemctl restart named
    SHELL
  end
end

