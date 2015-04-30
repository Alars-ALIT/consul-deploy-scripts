VAGRANTFILE_API_VERSION = "2"
APP_DIR = "/deployer"

$script = <<SCRIPT
echo "Bash provisioning.."
SCRIPT

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
	config.vm.box = 'docker-vagrant'
	config.vm.box_url = 'https://oss-binaries.phusionpassenger.com/vagrant/boxes/ubuntu-12.04.3-amd64-vbox.box' 
	config.vm.synced_folder "./", "/vagrant", disabled: true

	config.vm.provider :virtualbox do |vb|
		 config.vm.synced_folder "./", "#{APP_DIR}", create: true		
	end
	
	# Provision docker
	config.vm.provision :docker

	config.vm.define :deployer do |app|
		ip = "10.0.5.3"
		app.vm.hostname = "deployer"
		hostname = app.vm.hostname
		app.vm.network :private_network, ip: ip					

		# Provision 
		config.vm.provision :shell, :inline => $script, :args => [ip, hostname]
	end
	
end