# -*- mode: ruby -*-
# vi: set ft=ruby :
$script = <<SCRIPT

echo Installing epel repo
sudo yum -y install epel-release
sudo yum -y install cjdns

sudo mv /home/vagrant/cjdns.service /etc/systemd/system/cjdns.service

sudo systemctl enable cjdns
sudo systemctl start cjdns

SCRIPT

VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = "centos/7"
  config.vm.provision "file", source: "configs/cjdns.service", destination: "/home/vagrant/cjdns.service"

  config.vm.provider "virtualbox" do |v|
  v.memory = 512
  end

  config.vm.define "node1" do |node1|
      node1.vm.hostname = "node1"
      node1.vm.network "private_network", ip: "172.20.20.11"
      node1.vm.provision "file", source: "configs/cjdroute_n1.conf", destination: "/home/vagrant/cjdroute.conf"
      node1.vm.provision "shell", inline: $script
  end

  config.vm.define "node2" do |node2|
      node2.vm.hostname = "node2"
      node2.vm.network "private_network", ip: "172.20.20.12"
      node2.vm.provision "file", source: "configs/cjdroute_n2.conf", destination: "/home/vagrant/cjdroute.conf"
      node2.vm.provision "shell", inline: $script
  end

  config.vm.define "node3" do |node3|
      node3.vm.hostname = "node3"
      node3.vm.network "private_network", ip: "172.20.20.13"
      node3.vm.provision "file", source: "configs/cjdroute_n3.conf", destination: "/home/vagrant/cjdroute.conf"
      node3.vm.provision "shell", inline: $script
  end

  config.vm.define "node4" do |node4|
      node4.vm.hostname = "node4"
      node4.vm.network "private_network", ip: "172.20.20.14"
      node4.vm.provision "file", source: "configs/cjdroute_n4.conf", destination: "/home/vagrant/cjdroute.conf"
      node4.vm.provision "shell", inline: $script
  end
end
