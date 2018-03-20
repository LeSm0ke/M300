Vagrant.configure(2) do |config|
  config.vm.box = "debian/stretch64"
  config.vm.network "forwarded_port", guest:80, host:8080, auto_correct: true
  config.vm.synced_folder ".", "/var/www/html"
 config.vm.provider "virtualbox" do |vb|
  vb.memory = "512"
 end
  config.vm.provision "shell", inline: <<-SHELL
    sudo apt-get update
    sudo apt-get install apache2 php5 libapache2-mod-php5 -y
    sudo apt-get install mysql-server mysql-client php5-mysql -y
    sudo apt-get install phpmyadmin -y
    apt-get install openjdk-8-jre-headless -y
    apt-get install screen -y
    adduser minecraft
    mkdir minecraft
    cd minecraft
    wget https://yivesmirror.com/files/spigot/spigot-latest.jar
    screen -AmdS minecraft java -jar /home/minecraft/spigot-latest.jar
  SHELL
end