Vagrant.configure("2") do |config|
    config.vm.box = 'precise32'
    #config.vm.box_url = 'https://dl.dropboxusercontent.com/u/3428571/raring64.box'
    
    
    config.vm.box_url = "http://files.vagrantup.com/precise32.box"

    #config.vm.network :forwarded_port, guest: 80, host: 8080

    #config.vm.network :private_network, ip: "192.168.33.10"

          # config.vm.network :public_network

    
    config.vm.synced_folder "salt/", "/srv/salt" # Notice this difference

    config.vm.define :master do |master|
     
        master.vm.provision :salt do |s|
            s.minion_config = "master"
            s.verbose = true
            #s.run_highstate = true
            s.install_master = true
        end
        master.vm.hostname = "master"
        master.vm.network :private_network, ip: "192.168.12.13"
    end
    
    config.vm.define :minion do |minion|

    minion.vm.network :private_network, ip: "192.168.12.14"
    minion.vm.provision :salt do |s|
        s.minion_config = "minion"
        s.verbose = true
        s.run_highstate = true
    end
    minion.vm.hostname = "minion"
    end
end
