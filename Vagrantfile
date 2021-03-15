Vagrant.configure("2") do |config|
  config.vm.provision "shell", inline: "echo Hello"

  config.vm.define "lb" do |lb|
    lb.vm.box = "ubuntu/xenial64"
    lb.vm.network "private_network", ip: "192.168.33.8"
    lb.vm.provision "shell", path: "install_lb.sh"
    lb.disksize.size = '10GB'
    lb.vm.provider "virtualbox" do |v|
        v.memory = 2024
        v.cpus = 2
     end
  end

  config.vm.define "web1" do |web1|
    web1.vm.box = "ubuntu/xenial64"
    web1.vm.network "private_network", ip: "192.168.33.9"
    web1.vm.provision "shell", path: "install_web.sh"
  end

  config.vm.define "web2" do |web2|
    web2.vm.box = "ubuntu/xenial64"
    web2.vm.network "private_network", ip: "192.168.33.10"
    web2.vm.provision "shell", path: "install_web.sh"
  end

  config.vm.define "db" do |db|
    db.vm.box = "ubuntu/xenial64"
    db.vm.network "private_network", ip: "192.168.33.11"
    db.vm.provision "shell", path: "install_mysql.sh"
  end
end
