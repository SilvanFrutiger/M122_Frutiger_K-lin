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
Datei-Inhaltes|wc -1 Zieldatei||
wc|(word count) zählt Wörter oder Linien eines 
echo|Gibt eine Zeichenkette aus|echo "Zeichenkette"

### Dateirelevante Befehle
|Zeichen|Bedeutung|Beispiel|
---|---|---|
|alias|erstellt einen Alias für einen Befehl|alias aliasname="Befehl"|

### Wildcards und Brace extensions
|Zeichen|Bedeutung|Beispiel|
---|---|---|
*|steht für belibig viele Zeichen|ls *.txt
?|steht für ein belibiges Zeichen|ls file?.txt
{,}|erzeugt File1.txt, File2.txt und File3.txt|touch File{1,2,3}.txt
{..}|erzeugt einen Bereich|touch file{1..9}.txt
|!|schliesst einen Ausdruck aus der Suche aus|ls file{!ausdruck}.txt|
|{}|Verschachtelungen, Beispiel erzeugt die Files fileoriginal.txt, fileoriginal.bak, filekopie.txt und filekopie.baktouch| file{orginal{.bak,.txt},kopie{.bak,.txt}}|

### Tilde expansion
|Zeichen|Bedeutung|Beispiel|
---|---|---|
|~|Homeverzeichnis des aktiven Benutzers|~|
|~Benutzername|Homeverzeichnis des Users||
m~-|Zuvor besuchtes Verzeichnis||
~+|gibt den Pfad an|
