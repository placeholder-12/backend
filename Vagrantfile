# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
  config.vm.box = "ubuntu/trusty32"

  config.vm.network "forwarded_port", guest: 80, host: 8080
  config.vm.network "forwarded_port", guest: 443, host: 8888

  config.vm.synced_folder ".", "/vagrant", disabled: true
  config.vm.synced_folder "../DeliveryMan/", "/deliveryman"
  config.vm.synced_folder "../RepoMan", "/repoman"

  config.vm.provision "ansible" do |ansible|
      ansible.playbook = "ansible/playbook.yml"
      ansible.extra_vars = { deploy_mode: 'local'}
  end
end
