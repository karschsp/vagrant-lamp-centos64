# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant::Config.run do |config|
  config.vm.host_name = "dev.local"
  config.vm.network :hostonly, "192.168.56.60"
  config.vm.customize ["modifyvm", :id, "--memory", "2048"]
  config.vm.box = "vagrant-centos-64"
  config.vm.box_url = "http://stevekarsch.com/sites/default/files/vagrant-centos-64.box"
  config.ssh.forward_agent = true
  config.vm.forward_port 80, 81
  config.vm.share_folder "v-projects", "/projects", "./projects"

  config.vm.provision :puppet do |puppet|
    puppet.module_path = "modules"
    puppet.manifests_path = "manifests"
    puppet.manifest_file = "init.pp"
  end
end