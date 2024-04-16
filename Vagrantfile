# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure("2") do |config|
  # For a complete reference, please see the online documentation at
  # https://docs.vagrantup.com.

  # boxes at https://vagrantcloud.com/search.
  config.vm.box = "bento/ubuntu-22.04-arm64"

  # Disable automatic box update checking. If you disable this, then
  # boxes will only be checked for updates when the user runs
  # `vagrant box outdated`. This is not recommended.
  # config.vm.box_check_update = false

  config.vm.define "vm1" do |vm1|
    vm1.vm.network "private_network", ip: "192.168.25.10"
    vm1.vm.provider "vmware_fusion" do |v|
      #v.gui = true
      #v.vmx["memsize"] = "2048"
      #v.vmx["numvcpus"] = "4" 
    end
    vm1.vm.cloud_init :user_data do |cloud_init|
      cloud_init.content_type = "text/cloud-config"
      cloud_init.path = "cloud-init.cfg" # funktioniert nicht
    end
  end

##  config.vm.define "vm2" do |vm2|
##    vm2.vm.network "private_network", ip: "192.168.25.11"
##  end
##
##  config.vm.define "vm3" do |vm3|
##    vm3.vm.network "private_network", ip: "192.168.25.12"
##  end

  # Bridged networks make the machine appear as another physical device on
  # your network.
  # config.vm.network "public_network"

  # Disable the default share of the current code directory.
  # config.vm.synced_folder ".", "/vagrant", disabled: true

   config.vm.provision "shell", inline: <<-SHELL
     #sudo apt-get update && sudo apt-get upgrade -y
     curl -L https://github.com/seboknt.keys >> /home/vagrant/.ssh/authorized_keys
   SHELL
end
