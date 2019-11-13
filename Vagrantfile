# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "debian/contrib-buster64"

   config.vm.provider "virtualbox" do |vb|
     vb.gui = true
     # vb.memory = "1024"
     vb.customize ['setextradata', :id, 'GUI/ScaleFactor', '2']
   end

  config.vm.provision "shell", inline: <<-SHELL
    export DEBIAN_FRONTEND=noninteractive
    apt-get update
    apt-get -y upgrade
    apt-get -y dist-upgrade
    apt-get install -y libseccomp-dev libcap-dev libacl1-dev libselinux-dev libcap-ng-utils

    modprobe veth

    sed -i 's/^GRUB_TIMEOUT=.*/GRUB_TIMEOUT=60/' /etc/default/grub
    update-grub
  SHELL
end
