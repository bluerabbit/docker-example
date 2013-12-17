VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box     = "precise64"
  config.vm.box_url = "http://files.vagrantup.com/precise64.box"

  config.vm.provider :virtualbox do |vb|
    vb.name = "docker-example"
    vb.customize ["modifyvm", :id, "--memory", 1024]
  end

  config.vm.network "forwarded_port", guest: 8080, host: 8080

  config.vm.synced_folder "./share", "/home/vagrant/share", create: true, owner: 'vagrant', group: 'vagrant'

  config.vm.provision "docker" do |d|
    d.run "ubuntu", cmd: "bash -l", args: "-v '/vagrant:/var/www'"
  end
end
