# -*- mode: ruby -*-
# vi: set ft=ruby :

required_plugins = %w(vagrant-hosts vagrant-lxc)

required_plugins.each do |plugin|
  system "vagrant plugin install #{plugin}" unless Vagrant.has_plugin? plugin
end

VAGRANTFILE_API_VERSION = "2"
Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

  config.vm.box = "fgrehm/centos-6-64-lxc"

  config.ssh.insert_key = false

  config.vm.define 'gocd-server' do |instance|
    instance.vm.provision :hosts    
    instance.vm.provision 'ansible' do |ansible|
      ansible.playbook = 'playbook.yml'
      ansible.sudo = true
      ansible.groups = {
        'gocd-servers' => ['gocd-server']
      }
    end
  end

  config.vm.define 'gocd-agent' do |instance|
    instance.vm.provision :hosts    
    instance.vm.provision 'ansible' do |ansible|
      ansible.playbook = 'playbook.yml'
      ansible.sudo = true
      ansible.groups = {
        'gocd-agents' => ['gocd-agent']
      }
    end
  end

end
