# Übungen
## Übung 1

1. cd~

2. cd /var/log

3. cd /etc/udev

4. cd ./etc



## Übung 2

### Erzeugen Sie ein Verzeichnis Docs in ihrem Heimverzeichnis

touch

---
### Erstellen Sie die Dateien file1 bis file10 mit touch im Docs Verzeichnis
- touch file{1..10}.txt

---
### Löschen Sie alle Dateien, welche einer 1 im Dateinamen haben
- rm \*1*

---
### Löschen Sie file2, file4, file7 mit einem Befehl
- rm file{2, 4, 7}

---
### Löschen Sie alle restlichen Dateien auf einmal
- rm -r ./docs
---
### Erzeugen Sie ein Verzeichnis Files in ihrem Heimverzeichnis
- mkdir "Verzeichnisname"
- touch dateiname

---
### Erstellen Sie die Dateien file1 bis file10 mit touch im Files Verzeichnis
- touch file{1..10}

---
### Kopieren Sie das Verzeichnis Files mitsamt Inhalt nach Files2
mv -r \<verzeichnisname> \<neuesverzeichnis>

---
### Kopieren Sie das Verzeichnis Files mitsamt Inhalt nach Files2/Files3

mv -r \<files> \<files2>, \<files> \<files3> 

---
### Benennen Sie das Verzeichnis Files in Files1 um
mv -r \<Files1> \<Files>

---
### Löschen Sie alle erstellten Verzeichnisse und Dateien wieder
rm -r \<Verzeichnissname>
#### oder
rm -rf \<Verzeichnispfad>
löscht alles ohne rücksicht auf vorgaben.

## Übung 3

### Führen Sie jede in der Theorie aufgeführte Erweiterungen der Tilde einmal an Ihrem System aus und stellen Sie sicher, dass Sie deren Funktionsweisen verstanden haben.
|Zeichen|Bedeutung|Beispiel|
---|---|---|
|~|Homeverzeichnis des aktiven Benutzers|~|
|~Benutzername|Homeverzeichnis des Users||
m~-|Zuvor besuchtes Verzeichnis||
~+|gibt den Pfad an|

## Übung 4
### a) Erzeugen Sie eine Textdatei mit folgendem Inhalt:
mit touch die Datei erstellen und danach mit nano diese bearbeiten.
#### Alle Zeilen, welche obelix enthalten
cat \<Dateiname> | grep obelix
#### Alle Zeilen, welche 2 enthalten
cat \<Dateiname> | grep 2
#### Alle Zeilen, welche ein e enthalten
cat \<Dateiname> | grep e
#### Alle Zeilen, welche nicht gamma enthalten
cat \<Dateiname> | grep -v gamma
#### Alle Zeilen, welche 1, 2 oder 3 enthalten (benutzen Sie -E und eine regex)
cat \<Dateiname> | grep -E [1,2,3]

### b)  Gehen Sie von derselben Datei aus wie in Übung a). Benutzen Sie cut und formulieren Sie damit einen Befehl, um nur folgende Begriffe anzuzeigen:

#### Alle Begriffe vor dem ersten :-Zeichen
cat \<Dateiname> | cut -d ’:’ -f 1
#### Alle Begriffe zwischen den beiden :-Zeichen
cat \<Dateiname> | cut -d ’:’ -f 2
#### Alle Begriffe rechts des letzten :-Zeichen
cat \<Dateiname> | cut -d ’:’ -f 3

#### c)  Nur für Knobbler: Gehen Sie wieder von derselben Datei aus wie in Übung a). Benutzen Sie awk und formulieren Sie damit einen Befehl, um nur die Begriffe anzuzeigen, die sich zwischen dem letzten und dem zweitletzten :-Zeichen befinden. Sie kriegen das gleiche Resultat wie bei der zweiten Übung unter b), aber nun dynamisch und die Anzahl Separatoren spielt keine Rolle mehr.

awk -F ":" '{print $(NF-1)}' file.txt
#### oder
cat file.txt | awk -F ":" '{print $(NF-1)}'


## Übung 5
### Was macht folgender Ausdruck?
#### mesg | egrep '[0-9]{4}:[0-9]{2}:[0-9a-f]{2}.[0-9]'
Findet alle Zeilen, welche eine PCI-Adresse beinhalten

#### Was macht folgender Ausdruck? ifconfig | grep -oE '((1?[0-9][0-9]?|2[0-4][0-9]|25[0-5])\.){3}(1?[0-9][0-9]?|2[0-4][0-9]|25[0-5])'
Findet IP-Adressen der Netzwerk-Anschlüsse


## Übung 6
### a) Erzeugen Sie eine Textdatei mit folgendem Inhalt:
cat << END > datei.txt
a
b
c
d
e
END

### b) Die Ausführung von ls -z erzeugt einen Fehler (da es die Option -z nicht gibt). Starten Sie ls mit -z und leiten Sie die Fehler in eine Datei /root/errorsLs.log um.
ls -z 2> errorsLs.log

### c) Erzeugen Sie eine kl. Textdatei und füllen Sie diese mit Inhalt. Geben Sie die Textdatei mit cat aus und leiten Sie die Ausgabe wieder in eine neue Datei um. Benutzen Sie einmal > und einmal >> (mehrmals hintereinander). Untersuchen Sie die beiden Situationen, indem Sie jedesmal den Inhalt der Datei wieder ausgeben. Was pasSiert wenn Sie in dieselbe Datei umleiten wollen?
echo "sdfonsdodsf" > datei.txt
cat datei.txt > datei2.txt
cat datei.txt > datei2.txt
cat datei2.txt
cat datei.txt >> datei2.txt
cat datei.txt >> datei2.txt
cat datei2.txt
#### oder
cat datei.txt >> datei.txt

### d) Leiten Sie die Ausgabe von whoami in die Datei info.txt um
whoami > info.txt

### e) Hängen Sie die Ausgabe von id an die Datei info.txt an
id >> info.txt

### f) Leiten Sie die Datei info.txt als Eingabe an das Programm wc um und zählen Sie damit die Wörter (-w)
cat info-txt | wc -w

## Aufgabe 1
### Aufgabe 1.1 Erzeugt Benutzer anhand einer Liste von Benutzernamen in einer Textdatei (via Parameter angegebenen). Hinweis: Benutzen Sie useradd und cat.

Der Dateiname, welcher die Benutzernamen beinhaltet, wird mit $1
übergeben: z.B. "benutzer.txt"

Datei erstellen mit dem code 
#!/bin/bash
for user in $(cat tst.txt); do useradd $user; done

sudo ./Datei.sh nameliste

cat /etc/passwd, das zeigt alle user an

### Aufgabe 1.2 Fügt einen Benutzer anhand einer Liste von Gruppen in einer Textdatei (via Parameter angegebenen) den jeweiligen Gruppen hinzu. Hinweis: Benutzen Sie groupadd, usermod und cat. Achtung es gibt für jeden Benutzer jeweils eine Initial login group und mehrere Supplementary groups.

Der Dateiname, welcher die Gruppen beinhaltet, wird mit dem ersten Parameter $1 übergeben,
der Benutzernamen mit den zweiten Parameter $2.

#!/bin/bash
	for group in $(cat DateiGruppe); do
	    groupadd -f $group | usermod -a -G $group $DateiName #$2 ist username
	done

[user@host ~]$ [sudo] ./aufg2.sh gruppen.txt 'benutzer'

[user@host ~]$ cat /etc/passwd
[user@host ~]$ id 'benutzer'

### Augabe 1.3 Findet alle Dateien, welche einem (via Parameter angegebenen) Benutzer gehören und kopiert diese an den aktuellen Ort. Die kopierten Dateien werden zu einem tar.gz Archiv zusammengefasst und danach gelöscht. Die Archivdatei wird mit dem Benutzernamen und dem aktuellen Datum benannt. Hinweis: Benutzen Sie find, tar, rm und date.

Der Benutzername wird mit $1 übergeben. (Verzeichnis user anpassen)

#!/bin/bash
name=$1_$(date '+%y-%m-%d').tar.gz;
find /home/user/* -user $1 -exec cp {} /home/user/Docs/found/ \;
tar -zcvf /home/user/Docs/found/$name /home/user/Docs/found/;
find /home/user/Docs/found/ -type f ! -name $name -delete;

### Aufgabe 1.4 Ermittelt die eigene IP-Adresse und macht einen PING-Sweep für das Subnetz der eigenen IP. Gibt aus, welche Hosts up sind und speichert die IP-Adressen der Hosts in einer Textdatei. Hinweis: Benutzen Sie ping (oder fping), ifconfig und grep.

Das Tool fping muss installiert sein ([user@host ~]$ [sudo] apt-get install fping).

    #!/bin/bash
    for i in $( ifconfig | grep "inet" | grep -v "127.0.0.1" | cut -d ":" -f 2 | cut -d "." -f 1-3 ); do
        for k in $(seq 1 255); do
            fping -c 1 -t250 $i.$k 2>&1 |  grep " 0% " | cut -d " " -f 1 >ips.txt
        done
    done

    #alternative Lösung:
    fping -g -c 1 -t250 172.16.6.0/24 2>&1 | grep " 0% " | cut -d " " -f 1 ips.txt

### Aufgabe 2.1 Erstellen Sie einen Ordner /root/trash und erzeugen Sie einige Dateien darin. Erstellen Sie ein Skript, welches alle 5 Minuten die Dateien innerhalb von diesem Ordner löscht (für Infos siehe auch Link 3 im Anhang). Überprüfen Sie, ob ihr Skript korrekt eingerichtet ist, indem Sie nachsehen, ob die Files nach 5 Minuten gelöscht wurden.

    [root@host: ~]# [sudo] mkdir /root/trash
    [root@host: ~]# [sudo] touch /root/trash/file{1..10}
    [root@host: ~]# [sudo] nano /root/trash.sh
    
    
     #!/bin/bash
     rm /root/trash/*
    
    
    [root@host: ]# [sudo] chmod +x trash.sh
    [root@host: ]# [sudo] crontab -e
    
     */5 * * * * /root/trash.sh
    
    [root@host: ]# watch ls /root/trash  
    
    (Warten bis files verschwinden --erfolgreiche Ausführung)

### Aufgabe 2.2 Erstellen Sie ein Skript, mit welchem eine IP-Adressrange bannen oder unbannen können. Es gibt unterschiedliche Tools, womit Sie diese Funktionalität umsetzen können. Verwenden Sie das Internet zur Informationssuche.

IP wird als $1 übergeben, ban oder unban als $2.

    #!/bin/bash
    if [ $2 = "ban" ]; then
        echo "banning " $1
        iptables -A INPUT -s $1 -j DROP
    elif [ $2 = "unban" ];then
        echo "unbanning " $1
        iptables -D INPUT -s $1 DROP
    else
        echo "Verwendung:"
        echo "1.Arg: IP-Adresse" 
        echo "2.Arg.: ban oder unban"  
        echo "Beispiel: ./ban.sh 192.168.13.3 ban"
    fi



### Aufgabe 2.3 Erstellen Sie folgende Benutzer und Gruppen. Benutzen Sie zur Automatisierung die Skripte aus den Übungen. Versuchen Sie den Prozess der Erstellung möglichst stark zu automatisieren:

### Aufgabe 2.4 Erstellen Sie folgende Ordnerstruktur und setzen Sie die abgebildeten Berechtigungen (Auf den Berechtigungen ist auch das SGID-Bit (s) und Sticky-Bit (T) abgebildet. Setzen Sie auch dieses. Sie finden eine Erklärung und Anleitung im zweiten Link zuunterst: