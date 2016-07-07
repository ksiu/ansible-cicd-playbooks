VAGRANTFILE_API_VERSION = "2"
box = 'ubuntu/trusty64'
url      = 'https://atlas.hashicorp.com/ubuntu/boxes/trusty64'

boxes = [
  {
    :name => 'jenkins',
    :ip   => '192.168.6.99',
    :guest_port => '8080',
    :host_port => '6080',
    :mem  => '1024',
    :cpu  => '1'
  },
  {
    :name => 'artifactory',
    :ip   => '192.168.6.98',
    :guest_port => '8080',
    :host_port => '9080',
    :mem  => '1024',
    :cpu  => '1'
  }
]

Vagrant.configure("2") do |config|
  config.vm.box = box
  config.vm.box_url = url
  config.ssh.insert_key = false

  boxes.each do |opts|
    config.vm.define opts[:name] do |config|
      config.vm.host_name = opts[:name]
      config.vm.network :forwarded_port, host: opts[:host_port] , guest: opts[:guest_port] 
	  config.vm.provider "virtualbox" do |v|
	    v.customize ["modifyvm", :id, "--memory", opts[:mem]]
	    v.customize ["modifyvm", :id, "--cpus", opts[:cpu]]
	  end
    end
  end
end

