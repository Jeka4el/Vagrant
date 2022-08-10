
Vagrant.configure(2) do |config|
  # образ системы Ubuntu 20.04 LTS
  config.vm.box = "ubuntu/focal64"
  # не проверять репозиторий на наличие обновлений
  config.vm.box_check_update = false

  # ПЕРВАЯ ВИРТУАЛЬНАЯ МАШИНА
  config.vm.define "srv-web" do |subconfig|
    # имя виртуальной машины
    subconfig.vm.provider "virtualbox" do |vb|
      vb.name = "srv-web"
    end
    # hostname виртуальной машины
    subconfig.vm.hostname = "srv-web"
    # настройки сети
    subconfig.vm.network "public_network", ip: "192.168.0.23", bridge: "enp4s0"
    # установка пакетов
    subconfig.vm.provision "nginx", type: "shell", inline: "echo Installing Nginx; apt update && apt-get install -y nginx"
  end

  # ВТОРАЯ ВИРТУАЛЬНАЯ МАШИНА
  config.vm.define "srv-db" do |subconfig|
    # имя виртуальной машины
    subconfig.vm.provider "virtualbox" do |vb|
      vb.name = "srv-db"
    end
    # hostname виртуальной машины
    subconfig.vm.hostname = "srv-db"
    # настройки сети
    subconfig.vm.network "public_network", ip: "192.168.0.25", bridge: "enp4s0"
    # установка пакетов
    # subconfig.vm.provision "mysql", type: "shell", inline: "apt-get install -y mysql-server"
  end
  
  # обновление системы (для первой и второй)
  # config.vm.provision "update", type: "shell", inline: "apt-get update && apt-get upgrade -y"
end
