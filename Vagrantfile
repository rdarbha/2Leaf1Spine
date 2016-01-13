require 'yaml'

Vagrant.configure("2") do |config|

  properties = YAML.load_file("properties.yml")
  config.vm.box = "CumulusVX-2.5.5"
  # ansible.groups = {
  #   "hosts" => [],
  #   "leafs" => []
  # }

  config.vm.define "leaf1" do |leaf1|
   leaf1.vm.network "private_network",  virtualbox__intnet: 'leaf1-leaf2'
   leaf1.vm.host_name = "leaf1"
   leaf1.vm.provision "ansible" do |ansible|
 #   ansible.extra_vars = {
 #     link_ip: "192.168.1.1/30",
 #     loopback_ip: "172.16.0.1"
 #   }
     ansible.playbook = "leafs-playbook.yml"
 #    ansible.playbook = "empty.yml"
   end
  end

  config.vm.define "leaf2" do |leaf2|
   leaf2.vm.network "private_network",  virtualbox__intnet: 'leaf1-leaf2'
   leaf2.vm.host_name = "leaf2"
   leaf2.vm.provision "ansible" do |ansible|
#    ansible.extra_vars = {
#      link_ip: "192.168.1.2/30",
#      loopback_ip: "172.16.0.2"
#    }
     ansible.playbook = "leafs-playbook.yml"
#     ansible.playbook = "empty.yml"
   end
  end

end
