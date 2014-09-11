# Vagrantfile to provision the
# stack required for the Ansible lamp-haproxy examples
# https://github.com/ansible/ansible-examples/tree/master/lamp_haproxy

VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

	# Pinch OpsCode centos6.5 box
	config.vm.box = "chef/centos-6.5"
	
	# Two web servers
	(1..2).each do |i|
  		config.vm.define "web#{i}" do |web|
      		web.vm.hostname = "web#{i}"
      		web.vm.network :private_network, ip: "192.168.3.#{i}"
  		end
  	end
  	
  	# Database servers
  	config.vm.define "db1" do |db1|
		db1.vm.hostname = "db1"
		db1.vm.network :private_network, ip: "192.168.4.1"
  	end
  	
  	# Load Balancers
  	config.vm.define "lb1" do |lb1|
		lb1.vm.hostname = "lb1"
		lb1.vm.network :private_network, ip: "192.168.5.1"
  	end
  	
  	# Monitoring / Nagios
  	config.vm.define "nagios" do |nagios|
		nagios.vm.hostname = "nagios"
		nagios.vm.network :private_network, ip: "192.168.6.1"
  	end
  	
  	# Provisioning with Ansible
  	config.vm.provision "ansible" do |ansible|
		ansible.playbook = "site.yml"
		ansible.sudo = true
	end
  	
	
end
