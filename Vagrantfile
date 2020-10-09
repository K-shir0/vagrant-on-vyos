Vagrant.configure("2") do |config|
  config.vm.box = "higebu/vyos"

  # config.vm.define :(マシン名 vagran状の名前)
  #  vyos.vm.hostname = ("仮想環境上での名前")
  #  vyos.vm.network :(ネットワーク形式 private_network, ), ip: "192.168.33.1", virtualbox__intnet: "intnet1"
  # end
  config.vm.define :vyos1 do | vyos |
    vyos.vm.hostname = "vyos1"
    vyos.vm.network :private_network, ip: "192.168.10.1", virtualbox__intnet: "intnet1"
  end

  # 2個目
  config.vm.define :vyos2 do | vyos |
    vyos.vm.hostname = "vyos2"
    vyos.vm.network :private_network, ip: "192.168.10.2", virtualbox__intnet: "intnet1"
    vyos.vm.network :private_network, ip: "192.168.20.2", virtualbox__intnet: "intnet2"
  end
  
  # 3個目
  config.vm.define :vyos3 do | vyos |
    vyos.vm.hostname = "vyos3"
   vyos.vm.network :private_network, ip: "192.168.20.3", virtualbox__intnet: "intnet2"
  end
end 
