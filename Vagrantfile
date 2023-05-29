Vagrant.configure("2") do |config|
  config.vm.box = "geerlingguy/centos7"
  config.vbguest.auto_update = false

  # vm
  config.vm.define "vm" do |vm|
    vm.vm.network "private_network", ip: "192.168.33.10"
    vm.vm.provider "virtualbox" do |vb|
      vb.memory = "4096"
      vb.cpus = "4"
    end

    vm.vm.provision "shell", inline: <<-SHELL
      yum update -y
      yum install httpd -y
      yum install mariadb-server
      systemctl start mariadb
      systemctl enable mariadb
      # mysql_secure_installation
    SHELL
  end
end