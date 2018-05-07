---


---

<h1 id="m300---dokumentation-von-ramon--caner">M300 - Dokumentation von Ramon &amp; Caner</h1>
<p>Im Modul 300 wurde uns die Arbeit mit Containers und Virtuellen Maschienen näher gebracht.<br>
Diese Dokumentation handelt über den start mit Docker.</p>
<h2 id="auftrag">Auftrag</h2>
<p>Unser Auftrag war es, verschiedene Services via Docker und GitHub zu realisieren. Mit Dockerkann man mit einem Docker-File einen Container erstellen ohne irgendwelche konfigurationen zu machen. Alles befindet sich in diesem File. Diesen Container kann man anschliessend laufen lassen.<br>
Dies bietet viele Vorteile.<br>
Container haben das Merkmal wenig Speicherplatz zu brauchen. Eine Virtuelle Maschine braucht viel Speicherplatz, der Container hingegen benötigt wenige hundert Megabytes.<br>
Bei der Containerisierung laufen nur die Dienste die wirklich benötigt werden. Das führt zu einer dezimierten Ressourcen Verschwendung und somit zu einer höheren Geschwindigkeit.</p>
<h2 id="bewertung">Bewertung</h2>
<p>• Umgebung funktionsfähig auf eigenem Notebook (Note 4.0)<br>
• Bestehende Docker Container kombinieren oder Container als Backend, Desktop App als Frontend (Note 4.5)<br>
• Eigene Container erstellen (Note 5.0 – 5.5)<br>
• Projekt auf github Ablegen und Dokumentieren (Markdown) (Note 5.5 – 6.0)</p>
<h2 id="unser-vorgehen">Unser Vorgehen</h2>
<p>Wir arbeiteten nach dem IPERKA system. Wir schauten uns den Auftrag genau an und informierten uns. Anschliessen planten wir unser Vorgehen. Die Vorgehensweise wurde vom Auftragsdokument übernommen, da dort alles genau beschrieben wurde. Wir arbeiteten somit das Skript durch. Zuerst versuchten wir die Docker umgebung auf Windows aufzusetzen, da Windows eine für uns sehr bekannte Umgebung war. Nach viel “herumgebastel” entschieden wir uns später auf einer VM Ubuntu zu installieren und Docker dort einzurichten.<br>
Da Docker ursprünglicherweise von der Linux Welt stammt, gelang es uns viel einfacher uns dort einzufinden.<br>
Schnell konnten wir erste Resultate erzielen.</p>
<h2 id="github">GITHUB</h2>
<p>Wir haben uns Konten bei GITHUB erstellt. GITHUB bietet die Möglichkeit Dateien auf einfachem Wege hochzuladen, leicht bearbeitbar und offen zugänglich zu machen.</p>
<p>Mit Github ist es möglich den Kontakt zu anderen Entwickler auf der ganzen welt zu aufzubauen. Genau auf diesem Wege werden wir auch unsere fertigen Vagrantfiles mit unserem Lehrer kommunizieren.</p>
<blockquote>
<p><em>“GitHub brings together the world’s largest community of developers to discover, share, and build better software.”</em></p>
</blockquote>
<h2 id="docker">Docker</h2>
<p>Docker bietet einem die Möglichkeit Container aufzusetzen und diese zu Verwalten.</p>
<p><strong>Docker</strong>  ist eine  Open Source-Software zur Isolierung von Anwendungen mit Containervirtualisierung.</p>
<blockquote>
<p><em>“Docker vereinfacht die Bereitstellung von Anwendungen, weil sich Container, die alle nötigen Pakete enthalten, leicht als Dateien transportieren und installieren lassen. Container gewährleisten die Trennung und Verwaltung der auf einem Rechner genutzten Ressourcen. Das beinhaltet laut Aussage der Entwickler: Code, Laufzeitmodul, Systemwerkzeuge, Systembibliotheken - alles was auf einem Rechner installiert werden kann”</em></p>
</blockquote>
<h2 id="eigener-service">Eigener Service</h2>
<p>Um einen Eigenen Service aufzusetzen haben wir verschiedene Dockerfiles angeschaut und versucht zu verstehen.<br>
Docker ist eigentlich sehr simpel aufgebaut. Man gibt einen Befehl an und danach was er genau machen soll.<br>
Hier ein kleines Beispiel:</p>
<pre><code>FROM ubuntu:14.04
</code></pre>
<p>Hier wird mit dem <code>FROM</code> Befehl gesagt, dass er das Image <code>Ubuntu</code> von dem Docker Repository herunterladen soll.<br>
mit <code>:14:04</code> geben wir die gewünschte Version an.<br>
Docker bietet einem viele vorgefertigte Images, die wir unter <a href="https://hub.docker.com/">https://hub.docker.com/</a> anschauen können.</p>
<p>Wie Sie hier sehen, haben wir im Moment keine Container.</p>
<p><img src="https://perrone.myqnapcloud.com:450/share.cgi/1_keine%20container.PNG?ssid=02YbC2K&amp;fid=02YbC2K&amp;path=%2FNeuer%20Ordner&amp;filename=1_keine%20container.PNG&amp;openfolder=normal&amp;ep=" alt="BILD 1"></p>
<p>Als erstes haben  das Hello-World ausgeführt um zu sehen ob Docker richtig installiert wurde.</p>
<p><img src="https://perrone.myqnapcloud.com:450/share.cgi/2_hello%20world.PNG?ssid=02YbC2K&amp;fid=02YbC2K&amp;path=%2FNeuer%20Ordner&amp;filename=2_hello%20world.PNG&amp;openfolder=normal&amp;ep=" alt="BILD 2"></p>
<p>Wir haben mit befehl **** den Containe rmit dem Apache Image gebuildet und diesen später mit befehl **** gestartet.<br>
Wie man sieht, sind wir nun im server drin.</p>
<p><img src="https://perrone.myqnapcloud.com:450/share.cgi/3_apache%20after%20build.PNG?ssid=02YbC2K&amp;fid=02YbC2K&amp;path=%2FNeuer%20Ordner&amp;filename=3_apache%20after%20build.PNG&amp;openfolder=normal&amp;ep=" alt="BILD 3"></p>
<h2 id="php">PHP</h2>
<p>Ebenfalls haben wir PHP Aufgesetzt.<br>
Dazu bin sind wir auf die Seite <a href="https://hub.docker.com/">https://hub.docker.com/</a> gegangen und haben uns die verschiedenen PHP unterstützende  Container angeschaut.<br>
Geeinigt haben wir uns auf <code>FROM php:7.0-apache</code> .</p>
<p>Wir haben ein einfaches PHP File angelegt und diesen in Ordner <code>SRC</code> getan.</p>
<pre><code>&lt;?php
echo "Pass de EFZ PHP";
</code></pre>
<p>Anschliessend haben wir ein leeres Dockerfile genommen und dieses so beschrieben:</p>
<pre><code>    FROM php:7.0-apache
COPY src/ /var/www/html/
EXPOSE 80
</code></pre>
<p>Dies Funktioniert ebenfalls</p>
<p><img src="https://perrone.myqnapcloud.com:450/share.cgi/4_PHP%20done.PNG?ssid=02YbC2K&amp;fid=02YbC2K&amp;path=%2FNeuer%20Ordner&amp;filename=4_PHP%20done.PNG&amp;openfolder=normal&amp;ep=" alt="BILD 4"></p>
<h2 id="testing">Testing</h2>
<p>Um das Testing durchzuführen haben wir verschiedene Testcases aufgeschrieben und nach diesen Fällen die Tests druchgeführt.<br>
Dokumentiert wurde ebenfalls das erwartete und das tatsächliche Ergebnis festgehalten.</p>
<p>| 	<strong>Test</strong>	 | <em>Erwartete Ausg.</em> | Tatächliche Ausg.</p>
<p>|  <strong>Docker Build</strong>  |  <em>Docker wird per <code>docker build -t Docker_NAME:Version . erstellt</code></em>  | Container ist nach CMD vorhanden</p>
<p>| 	<strong>Docker Verbinden</strong>	 | <em>Docker Container wird per <code>docker run -ti -p 80:80 NAME /bin/bash</code> gestartet</em> | Verbindung erfolgreich</p>
<p>| 	<strong>Port Forwarding</strong>	 | *Man kann auf 'Localhost’<em>und somit auf den Webserver zugreifen.</em> | Man kann auf ‘Localhost’*und somit auf den Webserver zugreifen.</p>
<p>| 	<strong>UFW Firewall</strong>	 | <em>Die Firewall wird installiert</em> | Die Firewall wird installiert</p>
<p><img src="https://ssl.gstatic.com/ui/v1/icons/mail/images/cleardot.gif" alt=""></p>

