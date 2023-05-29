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
      sudo yum install -y gcc g++ make automake autoconf curl-devel openssl-devel zlib-devel httpd-devel apr-devel apr-util-devel sqlite-devel
      cd /tmp
      curl -L --remote-name https://cache.ruby-lang.org/pub/ruby/3.0/ruby-3.0.2.tar.gz
      tar -xzvf ruby-3.0.2.tar.gz
      cd ruby-3.0.2
      ./configure
      make
      make install
      ruby --version

    SHELL
  end
end