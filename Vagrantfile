# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "debian/contrib-testing64"

  config.vm.provider "virtualbox" do |vb|
    vb.gui = true
    # vb.memory = "1024"
    vb.customize ['setextradata', :id, 'GUI/ScaleFactor', '2']
  end

  config.vm.provision "shell", inline: <<-SHELL
    export DEBIAN_FRONTEND=noninteractive
    apt-get update
    apt-get -y upgrade
    apt-get install -y build-essential libseccomp-dev libcap-dev libacl1-dev libselinux-dev libcap-ng-utils vim neovim python3 python3-pip curl

    modprobe veth

    sed -i 's/^GRUB_TIMEOUT=.*/GRUB_TIMEOUT=10/' /etc/default/grub
    update-grub

    wget https://dl.google.com/go/go1.13.4.linux-amd64.tar.gz
    tar -C /usr/local -xzf go1.13.4.linux-amd64.tar.gz
    echo 'export PATH=$PATH:/usr/local/go/bin' >> /etc/profile
    rm go1.13.4.linux-amd64.tar.gz

    wget https://github.com/exercism/cli/releases/download/v3.0.13/exercism-3.0.13-linux-x86_64.tar.gz
    tar -xzf exercism-3.0.13-linux-x86_64.tar.gz
    rm exercism-3.0.13-linux-x86_64.tar.gz
    mv exercism /usr/local/bin

    su -c "curl vimfiles.luan.sh/install | bash" vagrant

  SHELL
end
