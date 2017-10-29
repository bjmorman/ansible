# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.define "win2012r2" do |win|
    win.vm.box = "trueability/windows-server-2012-r2"
    win.vm.network "forwarded_port", guest: 5985, host: 55985
    win.vm.synced_folder "./", "/vagrant"
    win.vm.provider :virtualbox do |vbox|
      vbox.gui = false
      vbox.customize ["modifyvm", :id, "--memory", 2048]
      vbox.customize ["modifyvm", :id, "--cpus", 2]
    end
    win.vm.provision "ansible" do |ansible|
#      ansible.become = true
#      ansible.become_user = "administrator"
      ansible.raw_arguments = "--inventory=./hosts"
      ansible.playbook = "site.yaml"
    end
  end
end
