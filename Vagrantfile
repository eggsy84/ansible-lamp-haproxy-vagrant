# Vagrantfile to provision the
# stack required for the Ansible lamp-haproxy examples
# https://github.com/ansible/ansible-examples/tree/master/lamp_haproxy

VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

	# Pinch OpsCode centos6.5 box
	config.vm.box = "chef/centos-6.5"
	
	# Make use of hostname manager
	config.hostmanager.enabled = true
	
	# Two web servers
	(1..2).each do |i|
  		config.vm.define "web#{i}" do |web|
      		web.vm.hostname = "web#{i}"
  		end
  	end
  	
  	# Database servers
  	config.vm.define "db1" do |db1|
		db1.vm.hostname = "db1"
  	end
  	
  	# Load Balancers
  	config.vm.define "lb1" do |lb1|
		lb1.vm.hostname = "lb1"
  	end
  	
  	# Monitoring / Nagios
  	config.vm.define "nagios" do |nagios|
		nagios.vm.hostname = "nagios"
  	end
  	
  	# Provisioning with Ansible
  	config.vm.provision "ansible" do |ansible|
		ansible.playbook = "site.yml"
	end
  	
	
end
