IMAGE_NAME = "bento/ubuntu-18.04"

Vagrant.configure("2") do |config|
    config.ssh.username = "vagrant"
    config.ssh.password = "vagrant"
    config.ssh.insert_key = true

    config.vm.provider "virtualbox" do |v|
        v.memory = 4096
        v.cpus = 2
    end
      
    config.vm.define "HLF2" do |hlf|
        hlf.vm.box = IMAGE_NAME
        hlf.vm.network "private_network", ip: "192.168.50.10"
        hlf.vm.hostname = "hyperledger-fabric-2"
        hlf.vm.provision "ansible" do |ansible|
            ansible.playbook = "software-playbook.yml"
            ansible.extra_vars = {
                node_ip: "192.168.50.10",
            }
        end
    end
  
end
