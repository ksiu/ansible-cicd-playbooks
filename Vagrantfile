VAGRANTFILE_API_VERSION = "2"
box = 'ubuntu/trusty64'
url      = 'https://atlas.hashicorp.com/ubuntu/boxes/trusty64'

boxes = [
  {
    :name => 'jenkins',
    :ip   => '192.168.6.99',
    :mem  => '1024',
    :cpu  => '1'
  },
  {
    :name => 'artifactory',
    :ip   => '192.168.6.98',
    :mem  => '1024',
    :cpu  => '1'
  }
]

Vagrant.configure("2") do |config|
  config.vm.box = box
  config.vm.box_url = url

  boxes.each do |opts|
    config.vm.define opts[:name] do |config|
      config.vm.host_name = opts[:name]
      config.vm.network "private_network", ip:opts[:ip] 
	  config.vm.provider "virtualbox" do |v|
	    v.customize ["modifyvm", :id, "--memory", opts[:mem]]
	    v.customize ["modifyvm", :id, "--cpus", opts[:cpu]]
	  end
    end
  end
end

