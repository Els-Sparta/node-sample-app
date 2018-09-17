# Allows you to simply run vagrant up
required_plugins = ["vagrant-hostsupdater"]
# Run a loop through each of the plugins you stated in required_plugins array
required_plugins.each do |plugin|
  # executes the vagrant install plugin linking to line 2 code. It also checks if the plugin already exists
  exec "vagrant plugin install #{plugin}" unless Vagrant.has_plugin? (plugin)
end
# Run a method in ruby using vagrant version 2
Vagrant.configure("2") do |config|
  # Setting up the machine in ubuntu
  config.vm.box = "ubuntu/xenial64"
  # give it a private ip address
  config.vm.network("private_network", ip: "192.168.10.100")
  # A Vagrant plugin that manages hosts files within a multi-machine environment. It changes the file /etc/host
  config.hostsupdater.aliases = ["development.local"]
end
