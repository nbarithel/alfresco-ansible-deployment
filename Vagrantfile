user     = ENV['NEXUS_USERNAME']
pass     = ENV['NEXUS_PASSWORD']

Vagrant.configure("2") do |config|
  config.vm.box = "centos/7"
  config.vm.network "private_network", ip: "172.100.100.100"
  config.vm.provider "virtualbox" do |v|
    v.memory = 10240
    v.cpus = 4
  end
  config.vm.provision :ansible_local do |ansible|
    ansible.playbook = "playbooks/acs.yml"
    ansible.inventory_path = "inventory.yml"
    ansible.version = "2.9.15"
    ansible.limit = "all"
    ansible.become = true
    ansible.extra_vars = {
      nexus_user: user,
      nexus_password: pass
    }
  end
end