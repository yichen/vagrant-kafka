# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

MEMORY = 3072

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
	config.vm.hostname = 'kafka-cluster-vm'
  config.vm.box = "hashicorp/precise64"
  config.vm.define :kafkaclustervm do |t|
  end

  config.vm.provision :shell, path: "vagrant/provision.sh"

  config.vm.network "private_network", ip: "192.168.100.67"

  # zookeeper cluster with 5 nodes
  config.vm.network :forwarded_port, guest: 2181, host: 2181
  config.vm.network :forwarded_port, guest: 2182, host: 2182
  config.vm.network :forwarded_port, guest: 2183, host: 2183
  config.vm.network :forwarded_port, guest: 2184, host: 2184
  config.vm.network :forwarded_port, guest: 2185, host: 2185

  # Kafka cluster with 5 nodes
  config.vm.network :forwarded_port, guest: 9091, host: 9091
  config.vm.network :forwarded_port, guest: 9092, host: 9092
  config.vm.network :forwarded_port, guest: 9093, host: 9093
  config.vm.network :forwarded_port, guest: 9094, host: 9094
  config.vm.network :forwarded_port, guest: 9095, host: 9095

  config.vm.provider "vmware_fusion" do |v|
    v.vmx["memsize"] = MEMORY.to_s
  end
  config.vm.provider "virtualbox" do |v|
    v.memory = MEMORY
  end
end
