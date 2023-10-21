# -*- mode: ruby -*-
# vi: set ft=ruby :

env = YAML.load_file('environment.yml')

Vagrant.configure("2") do |config|

    env.each do |env|
      config.vm.define env['name'] do |srv|
        srv.vm.box      = env['box']
        srv.vm.hostname = env['hostname']
        srv.vm.network 'private_network', ip: env['ipaddress']
        #srv.ssh.insert_key = false
        #srv.ssh.private_key_path = ['~/.vagrant.d/insecure_private_key', '~/.ssh/id_rsa']
        #srv.vm.provision "file", source: "~/.ssh/id_rsa.pub", destination: "~/.ssh/authorized_keys"
        srv.vm.provider 'virtualbox' do |vb|
          #Adiciona em um grupo as VMs, no VirtualBox
          vb.customize ["modifyvm", :id, "--groups", "/wazuh"]
          vb.name   = env['name']
          vb.memory = env['memory']
          vb.cpus   = env['cpus']
        end
      end
    end
  end