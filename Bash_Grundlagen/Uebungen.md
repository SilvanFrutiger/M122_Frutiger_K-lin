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