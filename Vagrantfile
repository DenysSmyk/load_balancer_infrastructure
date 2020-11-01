# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|


  config.vm.define :lb do |lb|
    lb.vm.provider :virtualbox do |v|
      v.memory = 512
      v.cpus = 1
    end
    lb.vm.box = "hashicorp/bionic64"
    lb.vm.hostname = "lb"
    lb.vm.network :private_network, ip: "192.168.50.3"
    lb.vm.provision :ansible do |ansible|
      ansible.raw_arguments = ["--connection=paramiko", "--ask-pass", "-u vagrant"] 
      ansible.playbook = "./playbook_nginx.yml"
      #ansible.inventory_path = "./nginx.txt"
    end
  end


  %w{web1 web2}.each_with_index do |name, i|
    config.vm.define name do |web|
      web.vm.provider :virtualbox do |v|
        v.memory = 512
        v.cpus = 1
      end
      web.vm.box = "hashicorp/bionic64"
      web.vm.hostname = name
      web.vm.network :private_network, ip: "192.168.50.#{i + 4}"
      web.vm.provision :ansible do |ansible|
        #ansible.limit = "web"
        ansible.raw_arguments = ["--connection=paramiko", "--ask-pass", "-u vagrant"] 
        ansible.playbook = "./playbook_web_servers.yml"
        #ansible.inventory_path = "./web.txt"
      end
    end
  end

end
