Vagrant.configure("2") do |config|
	config.vm.box = "precise32"
	config.vm.box_url = "http://files.vagrantup.com/precise32.box"

	config.vm.network :private_network, ip: "192.168.57.111"

	config.vm.provider :virtualbox do |v|
		v.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
		v.customize ["modifyvm", :id, "--memory", 512]
		v.customize ["modifyvm", :id, "--name", "occur-vm"]
	end

	config.vm.synced_folder "./", "/var/www/app", id: "vagrant-root", :owner => "www-data"

	config.vm.provision "ansible" do |ansible|
		ansible.playbook = "ansible/provision.yml"
	end

end
