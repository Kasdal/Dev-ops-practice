Vagrant.configure("2") do |config|     #Provisioned machine names, Ip etc..
    servers=[
        {
          :hostname => "main",
          :box => "bento/ubuntu-18.04",
          :ip => "172.16.1.50",
          :ssh_port => '2200'
        },
        {
          :hostname => "server1",
          :box => "bento/ubuntu-18.04",
          :ip => "172.16.1.51",
          :ssh_port => '2201'
        },
        {
          :hostname => "server2",
          :box => "bento/ubuntu-18.04",
          :ip => "172.16.1.52",
          :ssh_port => '2202'
        },
        {
          :hostname => "server3",
          :box => "bento/ubuntu-18.04",
          :ip => "172.16.1.53",
          :ssh_port => '2203'
        }
      ]

    servers.each do |machine|
        config.vm.define machine[:hostname] do |node|
            node.vm.box = machine[:box]
            node.vm.hostname = machine[:hostname]
            node.vm.network :private_network, ip: machine[:ip]
            node.vm.network "forwarded_port", guest: 22, host: machine[:ssh_port], id: "ssh"
            node.vm.provider :virtualbox do |vb|
                vb.customize ["modifyvm", :id, "--memory", 512]   #specs of the provisioned machines
                vb.customize ["modifyvm", :id, "--cpus", 1]
            end
        end
    end
end