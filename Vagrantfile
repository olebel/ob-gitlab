# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = '2'

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

  config.vm.box = 'bento/centos-6.9'

  config.vbguest.auto_update = false
  config.omnibus.chef_version = "12.19.36"

  config.vm.define "ob_gitlab" do |ob_gitlab|
    ob_gitlab.vm.hostname = 'ob-gitlab.local'
    ob_gitlab.vm.network "forwarded_port", guest: 80, host: 3080
    ob_gitlab.vm.network "forwarded_port", guest: 443, host: 3443
    ob_gitlab.vm.provision 'chef_solo' do |chef|
      chef.add_recipe 'ob-gitlab'
      chef.nodes_path = './.vagrant/nodes'
    end
  end
end
