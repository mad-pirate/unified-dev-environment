# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/xenial64"

  # Networking
  config.vm.network "forwarded_port", guest: 80, host: 8080
  config.vm.network "private_network", ip: "192.168.50.10"

  # Files
  config.vm.synced_folder "./../applications", "/var/www/applications", create: true, owner: "vagrant", group: "vagrant", mount_options: ["dmode=775", "fmode=774"]

  # Provisioning
  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "environment.yml"
    ansible.raw_arguments = ["-e ansible_python_interpreter=/usr/bin/python3"]
  end
end
