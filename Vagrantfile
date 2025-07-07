Vagrant.configure("2") do |config|
  config.vm.box = "kalilinux/rolling"
  config.vm.hostname = "dvwa"
  config.vm.provider "virtualbox" do |vb|
    vb.memory = "4096"
    vb.cpus = 2
  end
  config.vm.post_up_message = <<-MESSAGE
  The DVWA VM has been created. 
  After the shell script configures the system, visit http://192.168.56.10/dvwa/setup.php
  Then click "Create / Reset Database" to begin.
  MESSAGE
  
  config.vm.provision "shell", inline: <<-SHELL
    echo "[*] Cloning DVWA repo..."
    git clone https://github.com/digininja/DVWA.git /var/www/html/dvwa

    echo "[*] Setting permissions"
    chown -R www-data:www-data /var/www/html/dvwa
    chmod -R 755 /var/www/html/dvwa

    echo "[*] Prepping config file"
    cp /var/www/html/dvwa/config/config.inc.php.dist /var/www/html/dvwa/config/config.inc.php

    echo "[*] Starting database server"
    systemctl start mariadb
  
    echo "[*] Configuring database server"
    mysql -e "CREATE DATABASE dvwa;"
    mysql -e "CREATE USER 'dvwa'@'localhost' IDENTIFIED BY 'p@ssw0rd';"
    mysql -e "GRANT ALL ON dvwa.* TO 'dvwa'@'localhost';"
    mysql -e "FLUSH PRIVILEGES;"

    echo "[*] Reloading services"
    systemctl restart apache2
  SHELL
  end
end
