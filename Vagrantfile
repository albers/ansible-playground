# vi: set ft=ruby sw=2 :

ansible_ip = "172.17.177.77"
target_ip  = "172.17.177.88"

Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/xenial64"
  config.vm.box_check_update = false

  config.vm.define "target" do |machine|
    machine.vm.hostname = "target"
    machine.vm.network "private_network", ip: target_ip
    machine.vm.provision "shell", 
      inline: 'apt-get install -y python'
  end

  config.vm.define "ansible" do |machine|
    machine.vm.hostname = "ansible"
    machine.vm.network "private_network", ip: ansible_ip
    machine.vm.provision "ansible_local" do |ansible|
      ansible.playbook = "provisioning/playbook.yml"
      ansible.extra_vars = {
	target_ip: target_ip
      }
    end
  end
end
