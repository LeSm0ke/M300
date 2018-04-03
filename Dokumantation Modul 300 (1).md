
# M300 - Dokumentation von Ramon & Caner

  

Im Modul 300 wurde uns die Arbeit mit Containers und Virtuellen Maschienen näher gebracht.

  

## Auftrag

  

Unser Auftrag war es, verschiedene Services via Vagrant und GitHub zu realisieren. Mit Vagrant kann man mit einem Vagrant-File eine VM erstellen ohne irgendwelche konfigurationen zu machen. Alles befindet sich in diesem File.

  

## Bewertung

  

• Umgebung (Multi VM) funktionsfähig auf eigenem Notebook (Note 4.0)

• Bestehende VM aus Vagrant Cloud zum laufen bringen (Note 4.5)

• Eigener Service auf Basis IaC implementieren (Note 5.0 – 5.5)

• Projekt auf github Ablegen und Dokumentieren (Markdown) (Note 5.5 – 6.0)

  

## Unser Vorgehen

Wir arbeiteten nach dem IPERKA system. Wir schauten uns den Auftrag genau an und informierten uns. Anschliessen planten wir unser Vorgehen. Die Vorgehensweise wurde vom Auftragsdokument übernommen, da dort alles genau beschrieben wurde. Wir arbeiteten somit das Skript durch. Wir hatten Startprobleme, da es bei Ramon nicht geklappt hat Vagrant aufzusetzen. Wir lösten dieses Problem am zweiten Modultag, indem wir alles nochmals neu installierten. Nachdem folgte die Arbeit am Skript. Leider verstanden wir nicht ganz alles, was uns zu einem unseren Mitstiften führte, mit welchem wir ein Vagrant-File erstellten.

  

## GITHUB

Wir haben uns Konten bei GITHUB erstellt. GITHUB bietet die Möglichkeit Dateien auf einfachem Wege hochzuladen, leicht bearbeitbar und offen zugänglich zu machen.

Mit Github ist es möglich den Kontakt zu anderen Entwickler auf der ganzen welt zu aufzubauen. Genau auf diesem Wege werden wir auch unsere fertigen Vagrantfiles mit unserem Lehrer kommunizieren.

> *"GitHub brings together the world's largest community of developers to discover, share, and build better software."*

  

## Produktive Nutzung

  

  

Unsere Umgebung ist darauf aufgebaut, dass man mit wenigen Commands eine ganze VM Umgebung aufsetzen kann, die sich automatisch installiert und Konfiguriert.

Bsp. kann ein Informatiker, der mehrere VMs pro Tag aufsetzten muss sich sehr viel Arbeit, Zeit und Nerven sparen.

  

So kann er mit Git Bash in ein Verzeichnis gehen, wo sich ein Vagrant-File befindet. In diesem Verzeichnis kann er ganz einfach den command "vagrant up" ausführen und das Vagrant-File wird ausgeführt.

  

In diesem Vagrant-File ist definiert von wo er sich das OS grabben soll, welche konfigurationen er vornehemen soll und wie ist installiert wird.


## Eigener Service
Wir haben bei dem Auftrag des eigenen Services zuerst darauf geschaut, dass wir das Vagrantfile überhaupt verstehen. Durch logisches überlegen, konnten wir anpassungen in diesem File vornehmen.
Sie sehen gleich ein Vagrant-File bei dem Ubuntu mit einer Firewall Reproxy installiert wird. die Ports haben wir so abgeändert, dass jegliche kommunikation von der IP 10.0.2.2 zugelassen wird.
Ausserdem das Protokoll TCP über den Port 80 in jedem Fall zugelassen.
Um sicherzugehen, dass diese Commands auch ausgeführt werden, führen wir den Command *Force* ein.

    Vagrant.configure(2) do |config|   config.vm.box = "ubuntu/trusty64"   config.vm.network "private_network", ip:"192.168.56.1"   config.vm.network "forwarded_port", guest:80, host:8080, auto_correct: true   config.vm.synced_folder ".", "/var/www/html"  config.vm.provider "virtualbox" do |vb|   vb.memory = "512"  end   config.vm.provision "shell", inline: <<-SHELL
        sudo apt-get update
        sudo apt-get install apache2 -y
        sudo apt-get install ufw -y
        sudo ufw allow from 10.0.2.2 to any port 22
        sudo ufw allow 80/tcp
        sudo ufw --force enable
        sudo apt-get install libapache2-mod-proxy-html -y
        sudo apt-get install libxml2-dev -y
        a2enmod proxy
        a2enmod proxy_html
        a2enmod proxy_http/41
        sed -i '$aServerName localhost' /etc/apache2/apache2.conf
        service apache2 restart
        cd /etc/apache2/sites-enabled
        wget https://pastebin.com/raw/GbjFC2ii
        cp GbjFC2ii 001-reverseproxy.conf   SHELL end


## Testing

Um das Testing durchzuführen haben wir verschiedene Testcases aufgeschrieben und nach diesen Fällen die Tests druchgeführt.
Dokumentiert wurde ebenfalls das erwartete und das tatsächliche Ergebnis festgehalten.

| 	**Test**	 | *Erwartete Ausg.* | Tatächliche Ausg.


| **Erstellung VM** | *Nach ausführen des Vagrant files, wird die VM erstellt*. | Nach ausführen des Vagrant files, wird die VM erstellt.
![](https://perrone.myqnapcloud.com:450/share.cgi/187_Erstellun.PNG?ssid=02YbC2K&fid=02YbC2K&path=/&filename=187_Erstellun.PNG&openfolder=normal&ep=)


| **SSH Verbindung** | *Die Verbindung zu dieser VM ist mit SSH möglich.* |  Die Verbindung zu dieser VM ist mit SSH möglich.
![enter image description here](https://perrone.myqnapcloud.com:450/share.cgi/187_ssh.PNG?ssid=02YbC2K&fid=02YbC2K&path=/&filename=187_ssh.PNG&openfolder=normal&ep=)


|  **Firewall**  | *Die Firewall ist gestartet*. | Die Firewall ist gestartet.
![
](https://perrone.myqnapcloud.com:450/share.cgi/187_test%20firewall.PNG?ssid=02YbC2K&fid=02YbC2K&path=/&filename=187_test%20firewall.PNG&openfolder=normal&ep=)

|  **Betrieb**  |  *Die Website ist ansprechbar.*  |  Die Website ist ansprechbar.

![enter image description here](https://perrone.myqnapcloud.com:450/share.cgi/187_Ubuntu%20website.PNG?ssid=02YbC2K&fid=02YbC2K&path=/&filename=187_Ubuntu%20website.PNG&openfolder=normal&ep=)

 |  **Apache**  |  *Apache ist als Prozess sichtbar.*  | Apache ist als Prozess sichtbar.
![
](https://perrone.myqnapcloud.com:450/share.cgi/187_Apache.PNG?ssid=02YbC2K&fid=02YbC2K&path=/&filename=187_Apache.PNG&openfolder=normal&ep=)


![](https://ssl.gstatic.com/ui/v1/icons/mail/images/cleardot.gif)

