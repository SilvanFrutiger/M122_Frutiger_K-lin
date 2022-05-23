## [Original Repository](https://gitlab.com/ch-tbz-it/Stud/m122/-/tree/main/02_Bash_Grundl)

---

## Zeichen mit Bedeutung

### Command Line Tool 

|Zeichen|Bedeutung|Beispiel|
---|---|---|
|~|Kürzel für das Heimatverzeichnis (Home) ||
|;|Trennt einzelne Befehle in einer Zeile voneinander||
| \| |Verkettet einezelne Befehle in einer Zeile||
|#|leitet einen Kommentar ein||
|\ |Lässt einen Befehl auf der nächsten Zeile weiterfahren||
|&|Befehl wird im Hintergrund ausgeführt||

### Systemspezifische Befehle
|Zeichen|Bedeutung|Beispiel|
---|---|---|
|Reeboot, shutdown -r oder init 6|Startet das System neu||
|halt, shutdown -h, init 0 oderpoweroff|Schaltet das System ab||

### Verzeichnisrelevante Befehle
|Zeichen|Bedeutung|Beispiel|
---|---|---|
|cd|ändert das Verzeichnis|cd ./bilder|
|mkdir|erstellt ein neues Verzeichnis|mkdir Verzeichnisname|
|rmdir|löscht ein bestehendes Verzeichnis, das Verzeichnis muss Leer sein|rmdir Verzeichnisname|
|ls|Listet den Verzeichnisinhalt auf|ls Verzeichnisname|

### Dateirelevante Befehle
|Zeichen|Bedeutung|Beispiel|
---|---|---|
|cp|kopiert Dateien/Verzeichnisse|cp Quelldatei Zieldatei|
|rm|löscht Dateien/Verzeichnisse|rm Zieldatei|
mv|Benennt Datei um|mv altedatei neuedatei
touch|Erstellt eine neue leere Datei| touch Dateiname
cat|Gibt den Dateiinhalt aus|cat Zieldatei
Datei-Inhaltes|wc -1 Zieldatei
wc|(word count) zählt Wörter oder Linien eines 
echo|Gibt eine Zeichenkette aus|echo "Zeichenkette"
