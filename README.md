# 試験用VyOSのVirtualBox環境めんどくさい方向けVagrantで楽に構築する方法

# 試験用VyOSのVirtualBox環境構築めんどくさい方向け
その問題Vagrantで解決できます。

## 環境
- macOS
- VirtualBox & Vagrant

## 環境作成
### VagrantのPlugin導入
VagrantfileからVyOSの設定を変更できるプラグインをインストール。

windows10 & macOS 共通
```
$ vagrant plugin install vagrant-vyos
```

### Vagrantfileを記述
テキストエディタなどでVagrantfileを作成

Vagrantfile
```
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
```

### 起動
以下のコマンドをVagrantfileが入っているディレクトリで実行
```
$ vagrant up

別々に起動
(vagrant up マシン名)
$ vagrant up vyos1
```

## 入り方
```
(vagrant ssh マシン名)
$ vagrant ssh vyos1
```

## 終わらせ方
シャットダウン
```
$ vagrant halt
```

削除
```
$ vagrant destroy
```