Vagrant.configure(2) do |config|
config.vm.define :web do |web_config|
  web_config.vm.box = "ubuntu/trusty64"
  web_config.vm.box_version = "14.04"
  web_config.vm.network "public_network", ip: "192.168.1.46"
  web_config.vm.hostname = "web"
  web_config.vm.provider "virtualbox" do |vb|
   vb.customize ["modifyvm", :id, "--uart1", "0x3F8", "4"]
   vb.customize ["modifyvm", :id, "--uartmode1", "file", File::NULL]  
     # Customize the amount of memory on the VM:
     vb.memory = "512"
   end
   web_config.vm.provision :ansible do |ansible|
        ansible.playbook = "web/apache.yml"
   end
end

config.vm.define :mysql1 do |mysql1_config|
  mysql1_config.vm.box = "ubuntu/trusty64"
  mysql1_config.vm.box_version = "14.04"
  mysql1_config.vm.network "public_network", ip: "192.168.1.47"
  mysql1_config.vm.hostname = "mysql1"
  mysql1_config.vm.provider "virtualbox" do |vb|
  
     # Customize the amount of memory on the VM:
     vb.memory = "512"
   end
   mysql1_config.vm.provision :ansible do |ansible|
        ansible.playbook = "mysql/mysql.yml"
   end
 end
end
