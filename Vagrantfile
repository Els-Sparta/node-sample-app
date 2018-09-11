# Allows you to simply run vagrant up
system "vagrant plugin install vagrant-hostsupdater"
# To tell vagrant what version to run in, in this case 2
Vagrant.configure("2") do |config|
  # What system to run in
  config.vm.box = "ubuntu/xenial64"
  # give it a private ip address
  config.vm.network("private_network", ip: "192.168.10.100")
  # A Vagrant plugin that manages hosts files within a multi-machine environment.
  config.hostsupdater.aliases = ["development.local"]
end
