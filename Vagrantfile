
# -*- mode: ruby -*-
# vi: set ft=ruby :

nodes = [
	{ :hostname => 'vm1', :ip => '192.168.56.5', :memory => 4096, :cpu => 2, :boxname => "ubuntu1804" },
    
]

Vagrant.configure("2") do |config|
  nodes.each do |node|
      config.vm.box_check_update = false
      config.vm.define node[:hostname] do |nodeconfig|
          nodeconfig.vm.box = node[:boxname]
          nodeconfig.vm.hostname = node[:hostname]
	  nodeconfig.vm.network :private_network, ip: node[:ip]
          nodeconfig.vm.provider :virtualbox do |vb|
            vb.memory = node[:memory]
            vb.cpus = node[:cpu]
          end
        end
  end

  config.vm.provision "shell", path: "script/postgres.sh"
  
  end
  


