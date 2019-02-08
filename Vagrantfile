# -*- mode: ruby -*-
# vi: set ft=ruby :
Vagrant.configure("2") do |config|
  config.vm.box = "centos/7"
  config.vm.network "forwarded_port", guest: 80, host: 8080, auto_correct: true

  config.vm.define 'centos' do |centos|
    centos.vm.hostname = 'centos'

    centos.vm.provision "ansible_local" do |ansible|
      ansible.playbook = 'main.yml'
    end

    centos.vm.provision :reload

    centos.vm.provision "ansible_local" do |ansible|
      ansible.playbook = 'after.yml'
    end
  end
end
