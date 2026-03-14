Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/jammy64"
  config.vm.box_check_update = false

  # Machine server-back (Spring Boot)
  config.vm.define "server-back" do |back|
    back.vm.hostname = "server-back"
    back.vm.network "private_network", ip: "192.168.33.20"
    back.vm.network "forwarded_port", guest: 8080, host: 8080  # Pour Spring Boot
    
    back.vm.provider "virtualbox" do |vb|
      vb.gui = true
      vb.memory = "2048"
      vb.cpus = "2"
      vb.name = "server-back"
    end
  end

  # Machine server-dba (MySQL)
  config.vm.define "server-dba" do |dba|
    dba.vm.hostname = "server-dba"
    dba.vm.network "private_network", ip: "192.168.33.21"
    dba.vm.network "forwarded_port", guest: 3306, host: 3308  # Port différent pour éviter conflits
    
    dba.vm.provider "virtualbox" do |vb|
      vb.gui = true
      vb.memory = "1024"
      vb.cpus = "1"
      vb.name = "server-dba"
    end
  end

  # Machine server-front (Nginx)
  config.vm.define "server-front" do |front|
    front.vm.hostname = "server-front"
    front.vm.network "private_network", ip: "192.168.33.22"
    front.vm.network "forwarded_port", guest: 80, host: 8081  # Nginx sur port 8081
    
    front.vm.provider "virtualbox" do |vb|
      vb.gui = true
      vb.memory = "1024"
      vb.cpus = "1"
      vb.name = "server-front"
    end
  end
end
