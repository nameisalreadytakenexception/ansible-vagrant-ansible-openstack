Vagrant.configure("2") do |config|
config.vm.box = "bento/ubuntu-18.04" #"v0rtex/xenial64" #"ubuntu/trusty64"
config.vm.define "openstack"
config.vm.synced_folder "provisioning", "/vagrant" 
config.vm.provider :virtualbox do |vb|
  vb.memory = "4096"
  vb.cpus = "2"
end

config.vm.provision "ansible_local" do |ansible|
  ansible.playbook = "openstack/playbook.yml"
  ansible.galaxy_roles_path = "openstack/openstack"
  ansible.limit          = "all"
  #ansible.inventory_path = "provisioning/openstack/hosts.txt"
end

config.vm.network :forwarded_port, guest: 80, host: 8080 
config.vm.network :private_network, ip: "" #   YOUR HOST IP
#config.vm.network :public_network, bridge: "eno1"
end