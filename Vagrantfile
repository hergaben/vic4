# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "debian/bullseye64"

  (1..4).each do |i|
    config.vm.define "debian#{i}" do |node|
      node.vm.hostname = "debian#{i}"

      # Статический IP
      node.vm.network "private_network", ip: "192.168.56.1#{i}"

      node.vm.synced_folder "./shared", "/home/vagrant/shared",
                            type: "rsync",
                            SharedFoldersEnableSymlinksCreate: false

      # File provisioner
      node.vm.provision "file",
                        source: "./scripts/hello.txt",
                        destination: "/home/vagrant/shared/hello.txt"
    end
  end
end
