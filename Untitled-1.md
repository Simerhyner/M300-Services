LB2

1.  Umgebung einrichten

    1.  VirtualBox

Die Applikation VirtualBox installieren.

Vagrant
-------

Die Applikation Vagrant installieren.

### VM erstellen

1.  Terminal (Git/Bash, muss davor installiert werden) öffnen

2.  In gewünschtem Verzeichnis einen neuen Ordner für die VM anlegen:

>   *\$ cd Wohin\\auch\\immer*

>   *\$ mkdir MeineVagrantVM*

>   *\$ cd MeineVagrantVM*

1.  Vagrantfile erzeugen, VM erstellen und entsprechend starten:

>   *\$ vagrant box add --name ubuntu/xenial64 \#Vagrant-Box hinzufügen*

>   *\$ vagrant init ubuntu/xenial64 \#Vagrantfile erzeugen*

>   *\$ vagrant up --provider virtualbox \#Virtuelle Maschine erstellen &
>   starten*

1.  Die VM ist nun in Betrieb (erscheint auch in der Übersicht innerhalb von
    VirtualBox) und kann via SSH-Zugriff bedient werden:

>   *\$ cd Pfad\\zu\\meiner\\Vagrant-VM \#Zum Verzeichnis der VM wechseln*

>   *\$ vagrant ssh \#SSH-Verbindung zur VM aufbauen*

1.  VM über VirtualBox-GUI ausschalten

    1.  Visualstudio Code

Die Applikation Visualstudio Code installieren.

Dem Editor folgende Extension hinzufügen:

-   Markdown All in One (von Yu Zhang)

-   Vagrant Extension (von Marco Stanzi)

-   vscode-pdf Extension (von tomiko1207)

Mit *ctrl* + *,* in die Einstellungen gehen und dort beim Abschnitt

// Configure glob patterns for excluding files and folders. For example, the
files

explorer decides which files and folders to show or hide based on this setting.

Read more about glob patterns here. (...)

Folgenden Code einfügen:

// Konfiguriert die Globmuster zum Ausschließen von Dateien und Ordnern.

"files.exclude": {

"\*\*/.git": true,

"\*\*/.svn": true,

"\*\*/.hg": true,

"\*\*/.vagrant": true,

"\*\*/.DS_Store": true

},

 GitHub
-------

Um GitHub zu nutzen muss man einen Account auf
[www.github.com](http://www.github.com) erstellen.

### Repository erstellen

1.  Anmelden unter www.github.com

2.  Innerhalb der Willkommens-Seite auf Start a project klicken

3.  Unter Repository name einen Name definieren (z.B. M300-Services)

4.  Optional: kurze Beschreibung eingeben

5.  Radio-Button bei Public belassen

6.  Haken bei Initialize this repository with a README setzen

7.  Auf Create repository klicken

    1.  SSH-Key

Als erstes muss man Git/Bash installieren. Danach werden die Befehle dort
ausgeführt.

1.  Terminal (Bash) öffnen

2.  Folgenden Befehl mit der Account-E-Mail von GitHub einfügen:

*ssh-keygen -t rsa -b 4096 -C "beispiel\@beispiel.com"*

1.  Neuer SSH-Key wird erstellt:

*Generating public/private rsa key pair.*

1.  Bei der Abfrage, unter welchem Namen der Schlüssel gespeichert werden soll,
    die Enter-Taste drücken (für Standard):

*Enter a file in which to save the key (\~/.ssh/id_rsa): [Press enter]*

1.  Nun kann ein Passwort für den Key festgelegt werden. Ich empfehle dieses zu
    setzen und anschliessend dem SSH-Agent zu hinterlegen, sodass keine erneute
    Eingabe (z.B. beim Pushen) notwendig ist:

*Enter passphrase (empty for no passphrase): [Passwort]*

*Enter same passphrase again: [Passwort wiederholen]*

1.  Datei %HOME%/.ssh/id_rsa.pub oder \$HOME/.ssh/id_rsa.pub in Zwischenablage
    kopieren.

2.  Anmelden unter www.github.com

3.  Auf Benutzerkonto klicken (oben rechts) und den Punkt Settings aufrufen

4.  Unter den Menübereichen auf der linken Seite zum Abschnitt SSH und GPG keys
    wechseln

5.  Auf New SSH key klicken

6.  Im Formular unter Title eine Bezeichnung vergeben (z.B. MB SSH-Key)

7.  Den zuvor kopierten Key mit CTRL + V einfügen und auf Add SSH key klicken

8.  Der Schlüssel (SSH-Key) sollte nun in der übergeordneten Liste auftauchen

    1.  Git-Client

9.  Git-Client installieren

10. Terminal (Bash) öffnen

11. Git konfigurieren mit Informationen des GitHub-Accounts:

*git config --global user.name "\<username\>"*

>   *git config --global user.email "\<e-mail\>"*

1.  Vagrant

    1.  VM aus Vagrant einrichten

Wie ich die VM eingerichtet habe ist bereits 1.2.1 dokumentiert.

Wichtige Befehle
----------------

| **Befehl**      | **Beschreibung**                                                                                                  |
|-----------------|-------------------------------------------------------------------------------------------------------------------|
| vagrant init    | Initialisiert im aktuellen Verzeichnis eine Vagrant-Umgebung und erstellt, falls nicht vorhanden, ein Vagrantfile |
| vagrant up      | Erzeugt und Konfiguriert eine neue Virtuelle Maschine, basierend auf dem Vagrantfile                              |
| vagrant ssh     | Baut eine SSH-Verbindung zur gewünschten VM auf                                                                   |
| vagrant status  | Zeigt den aktuellen Status der VM an                                                                              |
| vagrant port    | Zeigt die Weitergeleiteten Ports der VM an                                                                        |
| vagrant halt    | Stoppt die laufende Virtuelle Maschine                                                                            |
| vagrant destroy | Stoppt die Virtuelle Maschine und zerstört sie.                                                                   |

Umgebung
--------

Die Umgebung ist eine Standard ubuntu/xenial64 Version mit dem Benutzer vagrant
und dem Passwort vagrant. Da dies sonst eine Standardinstallation ist gibt es
die gesammte Dokumentation unter
<https://help.ubuntu.com/16.04/serverguide/index.html>.

Weitere VM
----------

Zudem habe ich auch noch eine Debian und CentOS Maschine mit Vagrant aufgesetzt.

Zusätzliches
------------

Zudem habe ich eine eigene Vagrantbox erstellt und auf Vagrant hochgeladen.

Mit dem Befehl kann man seine eigene Box erstellen:

*vagrant package --output mynew.box*

Mit diesem fügt man sie dem Vagrantinstaller zu:

*vagrant box add mynewbox mynew.box*

Danach kann man sie ganz normal mit dem Befehl *vagrant init mynewbox*
installieren.

1.  Sicherheitsaspekte

    1.  Firewall

Ich habe die UFW Firewall gearbeitet.

Installation:

*sudo apt-get install ufw*

UFW Befehle:

-   Ufw status

-   Ufw enable

-   Ufw disable

-   Ufw allow (from/deny) (out/from) [IP] to any port [Nr.]

-   Ufw delete

Ich habe folgende Rules eingerichtet:

-   ufw allow 80/tcp \# Port 80 (HTTP) öffnen für alle

-   sudo ufw allow from [Meine-IP] to any port 22 \# Port 22 nur für den Host
    öffnen

Jedoch habe ich die Firewall wieder abgeschaltet, um sicher ohne Firewall
Einschränkungen arbeiten zu können.

Reverse Proxy
-------------

Dafür muss zuerst Apache mit ein paar Erweiterungen installiert werden.

Installation:

>   *sudo apt-get install apache2*

>   *sudo apt-get install libapache2-mod-proxy-html*

>   *sudo apt-get install libxml2-dev*

Danach folgende Module installieren:

>   *sudo a2enmod proxy*

>   *sudo a2enmod proxy_html*

>   *sudo a2enmod proxy_http*

Die Datei /etc/apache2/apache2.conf wie folgt ergänzen:

-   ServerName localhost

Danach Apache neustarten:

*sudo service apache2 restart*

Benutzer- & Rechteverwaltung
----------------------------

Es ist bereits eine Benutzer- & Rechteverwaltung eingerichtet

Die Benutzer stehen in der Datei /etc/passwd. Die Passwörter in der Datei
/etc/shadow.

Dateirechte kann man mit diesen Befehlen ändern:

| **Befehl** | **Funktion**                            |
|------------|-----------------------------------------|
| chmod      | Dient zum Setzen der Dateirechte        |
| chown      | Dient zum Ändern des Dateibesitzers     |
| chgrp      | Dient zum Ändern der Gruppe einer Datei |

Reflexion
=========

Bei diesem Projekt haben wir mit viel Neuem gearbeitet was großartig war, jedoch
wusste ich zu beginn nicht was genau ich machen sollte. Sonst war das Projekt
gut.

Was ich neues gelernt habe:

-   Vagrant

-   VisualStudio

Was ich repetiert habe:

-   Git

-   UFW

-   Reverse Proxy
