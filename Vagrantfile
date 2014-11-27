# -*- mode: ruby -*-

VAGRANTFILE_API_VERSION = '2'

$script = <<SCRIPT
apt-get update
apt-get install exim4 -y
SCRIPT

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = 'precise64'

  config.vm.box_url = 'http://files.vagrantup.com/precise64.box'

  config.vm.define 'aegir.gub.se', primary: true do |machine|
    machine.vm.network :private_network, ip: '192.168.33.10'

    machine.vm.provision :shell, inline: $script

    machine.vm.provision :ansible do |ansible|
      ansible.playbook = 'provisioning/playbook.yml'
      ansible.sudo = true
      ansible.limit = 'all'

      ansible.groups = {
        'hostmaster' => ['aegir.gub.se'],
      }

      ansible.extra_vars = {
        'default_interface' => 'eth1',
      }
    end
  end
end
