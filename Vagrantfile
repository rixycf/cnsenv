# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure("2") do |config|

  # use ubuntu 
  ## tinet is tested ubuntu 16.04 LTS and later
  config.vm.box = "bento/ubuntu-16.04"

  config.vm.provider "virtualbox" do |vb|
    # Customize the amount of memory on the VM:
    vb.memory = "2048"

  end

  ## tinet require docker  
  config.vm.provision "docker"

  ## install tinet and dependencies
  config.vm.provision "shell", inline: <<-SHELL
    apt install -y python3 python3-pip graphviz git linux-image-extra-virtual
    git clone https://github.com/slankdev/tinet tinet

    cd tinet
    pip3 install -r requirement.txt
    cp bin/tn /usr/local/bin/tn

    sudo modprobe mpls_router
    sudo modprobe mpls_gso
    sudo modprobe mpls_iptunnel
  SHELL
end
