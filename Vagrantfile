Vagrant.configure("2") do |config|
  config.hostmanager.enabled = true 
  config.hostmanager.manage_host = true
  config.vbguest.auto_update = false
  config.ssh.insert_key = false
  
  ### Ansible ###
config.vm.define "cdc" do |cdc|
  cdc.vm.box = "geerlingguy/ubuntu2004"
  cdc.vm.hostname = "cdc"
  cdc.vm.network "private_network", ip: "192.168.60.50", virtualbox__intnet: false
  cdc.vm.synced_folder ".\\vagrant_folder", "/vagrant"
  cdc.vm.provider "virtualbox" do |vb|
    # vb.gui = true
    vb.memory = "6000"
    vb.name = "cdc"
    vb.cpus = "4"
    vb.customize ["modifyvm", :id, "--uart1", "0x3F8", "4"]
    vb.customize ["modifyvm", :id, "--uartmode1", "file", File::NULL]
  end
  cdc.vm.provision "shell", path: ".\\vagrant_folder\\docker.sh"
end
end  
