Vagrant.configure("2") do |config|
    # Configuración de la máquina virtual
    config.vm.box = "ubuntu/bionic64" # Usa una versión de Ubuntu (puedes ajustar según necesites)
    
    # Configuración de recursos
    config.vm.provider "virtualbox" do |vb|
      vb.memory = "512"
      vb.cpus = 1
    end
    
    # Provisión de Apache
    config.vm.provision "shell", inline: <<-SHELL
      sudo apt-get update
      sudo apt-get install -y apache2
      echo "<h1>Hola Mundo</h1>" | sudo tee /var/www/html/index.html
      sudo systemctl restart apache2
    SHELL
    
    # Compartir carpeta de apache
    config.vm.synced_folder ".", "/var/www/html", type: "virtualbox"
    
    # Redireccionar el puerto
    config.vm.network "forwarded_port", guest: 80, host: 8080
  end
  
  