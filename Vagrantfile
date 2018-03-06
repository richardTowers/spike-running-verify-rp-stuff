# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/trusty64"

  config.vm.network "forwarded_port", guest: 50100, host: 8080

  config.vm.provision "file", source: "pki/signing-private-key.pk8", destination: "~/pki"
  config.vm.provision "file", source: "pki/encryption-private-key.pk8", destination: "~/pki"
  config.vm.provision "file", source: "vsp-start.sh", destination: "~"

  config.vm.provision "shell", path: "provision-vsp.sh"
end
