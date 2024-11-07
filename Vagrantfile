Vagrant.configure("2") do |config|
    # Usamos la imagen oficial de Ubuntu 20.04 como base
    config.vm.box = "ubuntu/focal64"
  
    # Asignamos 512MB de RAM y 1 CPU
    config.vm.provider "virtualbox" do |vb|
      vb.memory = "512"
      vb.cpus = 1
    end
  
    # Configuración para compartir un directorio local con la VM
    config.vm.synced_folder "./src", "/var/www/html"
  
    # Configuración de red: Accederemos a la VM por puerto 8080
    config.vm.network "forwarded_port", guest: 80, host: 8080
  
    # Provisionar la máquina para instalar Apache
    config.vm.provision "shell", inline: <<-SHELL
      sudo apt-get update
      sudo apt-get install -y apache2
      sudo systemctl enable apache2
      sudo systemctl start apache2
    SHELL
  end
  