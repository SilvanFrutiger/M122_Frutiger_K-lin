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
Datei erstellen mit dem code 
#!/bin/bash
for user in $(cat tst.txt); do useradd $user; done

sudo ./Datei.sh nameliste

cat /etc/passwd, das zeigt alle user an

