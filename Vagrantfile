# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure("2") do |config|
  config.vm.define "ansible" do |ansible|
    ansible.vm.box = "bento/ubuntu-16.04"
    ansible.vm.network :private_network, ip: "10.12.3.100", virtualbox__intnet: true
    ansible.vm.hostname = "ansible.local.com"
  end

#  config.vm.define "jenkins" do |jenkins|
#   jenkins.vm.box = "bento/ubuntu-16.04"
#   jenkins.vm.network "private_network",
#    ip: "10.12.3.101",
#    virtualbox__intnet: true
#   jenkins.vm.network "forwarded_port",
#    guest: 8080,
#    host:8080                                                                                                                                                                                                                                                                  
#   jenkins.vm.hostname = "jenkins.local.com"                                                                                                                                                                                                                                   
#  end                                                                                                                                                                                                                                                                          
                                                                                                                                                                                                                                                                                
#  config.vm.define "base" do |base|                                                                                                                                                                                                                                            
#   base.vm.box = "ubuntu16.04_ansible_base"                                                                                                                                                                                                                                    
#   base.vm.network "private_network",                                                                                                                                                                                                                                          
#    ip: "10.12.3.101",                                                                                                                                                                                                                                                         
#    virtualbox__intnet: true                                                                                                                                                                                                                                                   
#   base.vm.hostname = "base.local.com"                                                                                                                                                                                                                                         
#   base.vm.provision "file", source: "keys/id_rsa.pub", destination: "~/.ssh/authorized_keys"                                                                                                                                                                                  
#  end                                                                                                                                                                                                                                                                          
                                                                                                                                                                                                                                                                                
                                                                                                                                                                                                                                                                                
  config.vm.define "kubemaster" do |kubemaster|                                                                                                                                                                                                                                 
   kubemaster.vm.provider "virtualbox" do |vb|                                                                                                                                                                                                                                  
    vb.memory = "1024"                                                                                                                                                                                                                                                          
    vb.cpus = "2"                                                                                                                                                                                                                                                               
   end                                                                                                                                                                                                                                                                          
   kubemaster.vm.box = "ubuntu16.04_ansible_base"                                                                                                                                                                                                                               
   kubemaster.vm.network "private_network",                                                                                                                                                                                                                                     
    ip: "10.12.3.101",                                                                                                                                                                                                                                                          
    virtualbox__intnet: true                                                                                                                                                                                                                                                    
   kubemaster.vm.hostname = "kubemaster.local.com"                                                                                                                                                                                                                              
   kubemaster.vm.provision "file", source: "keys/id_rsa.pub", destination: "~/.ssh/authorized_keys"                                                                                                                                                                             
#   kubemaster.vm.customize ["modifyvm", :id, "--cpus", 2]                                                                                                                                                                                                                      
#   kubemaster.vm.customize ["modifyvm", :id, "--memory", 1024]                                                                                                                                                                                                                 
  end                                                                                                                                                                                                                                                                           
                                                                                                                                                                                                                                                                                
  config.vm.define "kubeslave" do |kubeslave|                                                                                                                                                                                                                                   
   kubeslave.vm.box = "ubuntu16.04_ansible_base"                                                                                                                                                                                                                                
   kubeslave.vm.network "private_network",
    ip: "10.12.3.102",
    virtualbox__intnet: true
   kubeslave.vm.hostname = "kubeslave.local.com"
   kubeslave.vm.provision "file", source: "keys/id_rsa.pub", destination: "~/.ssh/authorized_keys"
  end

  # The most common configuration options are documented and commented below.
  # For a complete reference, please see the online documentation at
  # https://docs.vagrantup.com.

  # Every Vagrant development environment requires a box. You can search for
  # boxes at https://vagrantcloud.com/search.

  # Disable automatic box update checking. If you disable this, then
  # boxes will only be checked for updates when the user runs
  # `vagrant box outdated`. This is not recommended.
  # config.vm.box_check_update = false

  # Create a forwarded port mapping which allows access to a specific port
  # within the machine from a port on the host machine. In the example below,
  # accessing "localhost:8080" will access port 80 on the guest machine.
  # NOTE: This will enable public access to the opened port
  # config.vm.network "forwarded_port", guest: 80, host: 8080

  # Create a forwarded port mapping which allows access to a specific port
  # within the machine from a port on the host machine and only allow access
  # via 127.0.0.1 to disable public access
  # config.vm.network "forwarded_port", guest: 80, host: 8080, host_ip: "127.0.0.1"

  # Create a private network, which allows host-only access to the machine
  # using a specific IP.
  # config.vm.network "private_network", ip: "192.168.33.10"

  # Create a public network, which generally matched to bridged network.
  # Bridged networks make the machine appear as another physical device on
  # your network.
  # config.vm.network "public_network"

  # Share an additional folder to the guest VM. The first argument is
  # the path on the host to the actual folder. The second argument is
  # the path on the guest to mount the folder. And the optional third
  # argument is a set of non-required options.
  # config.vm.synced_folder "../data", "/vagrant_data"

  # Provider-specific configuration so you can fine-tune various
  # backing providers for Vagrant. These expose provider-specific options.
  # Example for VirtualBox:
  #
   config.ssh.insert_key = false
   config.ssh.private_key_path = ["keys/id_rsa", "~/.vagrant.d/insecure_private_key"]
   config.vm.provider "virtualbox" do |vb|
  #   # Display the VirtualBox GUI when booting the machine
  #   vb.gui = true
  #
  #   # Customize the amount of memory on the VM:
     vb.memory = "512"
   end
  #
  # View the documentation for the provider you are using for more
  # information on available options.

  # Enable provisioning with a shell script. Additional provisioners such as
  # Puppet, Chef, Ansible, Salt, and Docker are also available. Please see the
  # documentation for more information about their specific syntax and use.
  # config.vm.provision "shell", inline: <<-SHELL
  #   apt-get update
  #   apt-get install -y apache2
  # SHELL
end
