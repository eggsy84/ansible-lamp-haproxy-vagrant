# Vagrantfile to provision the
# stack required for the Ansible lamp-proxy examples
# https://github.com/ansible/ansible-examples/tree/master/lamp_haproxy

VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

	# Pinch OpsCode centos6.5 box
	config.vm.box = "chef/centos-6.5"

    config.vm.provision "ansible" do |ansible|
        ansible.playbook = "site.yml"
    end
end
