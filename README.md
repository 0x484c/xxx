Vagrant.configure(2) do |config|
  config.vm.box = "bento/centos-6.7"
  config.ssh.insert_key = false
  config.vm.provider "virtualbox" do |vb|
    vb.cpus = 2
    vb.memory = 2048
  end

  config.vm.define :web1 do |web1_config|
      web1_config.vm.host_name = "web1"
      web1_config.vm.network "public_network", ip:"192.168.100.161"
      web1_config.vm.network "private_network", ip:"172.168.100.161"
  end

  config.vm.define :web2 do |web2_config|
      web2_config.vm.host_name = "web2"
      web2_config.vm.network "public_network", ip:"192.168.100.162"
      web2_config.vm.network "private_network", ip:"172.168.100.162"
  end

  config.vm.define :db1 do |db1_config|
      db1_config.vm.host_name = "db1"
      db1_config.vm.network "public_network", ip:"192.168.100.163"
      db1_config.vm.network "private_network", ip:"172.168.100.163"
  end

  config.vm.define :db2 do |db2_config|
      db2_config.vm.host_name = "db2"
      db2_config.vm.network "public_network", ip:"192.168.100.164"
      db2_config.vm.network "private_network", ip:"172.168.100.164"
  end
end

