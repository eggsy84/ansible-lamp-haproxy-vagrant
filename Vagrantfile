# Vagrantfile to provision the
# stack required for the Ansible lamp-haproxy examples
# https://github.com/ansible/ansible-examples/tree/master/lamp_haproxy

VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

	# Pinch OpsCode centos6.5 box
	config.vm.box = "chef/centos-6.5"
	
	# Two web servers
	(101..102).each do |i|
  		config.vm.define "web#{i}" do |web|
      		web.vm.hostname = "web#{i}"
      		web.vm.network :private_network, ip: "172.16.0.#{i}"
  		end
  	end
  	
  	# Database servers
  	config.vm.define "db" do |db|
		db.vm.hostname = "db"
		db.vm.network :private_network, ip: "172.16.0.103"
  	end
  	
  	# Load Balancers
  	config.vm.define "lb" do |lb|
		lb.vm.hostname = "lb"
		lb.vm.network :private_network, ip: "172.16.0.104"
  	end
  	
  	# Monitoring / Nagios
  	config.vm.define "nagios" do |nagios|
		nagios.vm.hostname = "nagios"
		nagios.vm.network :private_network, ip: "172.16.0.105"
		
		# Provisioning only on last machine since ansible deals with multiple hosts
		# See https://github.com/mitchellh/vagrant/issues/1784
  		nagios.vm.provision :ansible do |ansible|
    		ansible.playbook = "provisioning/site.yml"
    		ansible.inventory_path = "provisioning/inventory"
    		ansible.sudo = true
			ansible.verbose = "vvv"
  		end
		
  	end
  	
end
