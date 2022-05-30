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
|touch|neue Datei|touch Dateiname|

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

### Linux connection funktioniert nicht
1. sudo apt install openssh-server
2. sudo ufw status (falls der Port 21 aktiviert ist muss man Schritt 3. niht machen sondern erneut probieren zu verbinden)
3. sudo ufw allow ssh     
4. ssh Benutzername@IP-Adresse
   
### Variablen
|Zeichen|Bedeutung|Beispiel|
---|---|---|
|=|Variabel setzen|Variabel="InhaltVariabel"|
|$|auf Variabel zugreifen|$Variabel|
|=""|Variabel wird gelöscht|Varname=""|
|$()|ein zuauswertender ausdruck, z.B. Datum|Datum=$(date+ Y_M_D)|
|readonly|Varibel kann nicht mehr verändert werden|readonly var="Fester_Wert|
#### Vorgespeicherte
$LOGNAME 	Login-Name des Benutzers

$0 Der Name des aufgerufenen Shellscripts

$1 - $9, ${10}, ... ,  $* Parameter des aufgerufenen Shellscripts

$# Anzahl Parameter des aufgerufenen Shellscripts

$$ Die Prozessnummer des aufgerufenen Shellscripts

$? Der Beendigungsstatus eines Shellscripts

$! Die Prozessnummer des zuletzt gestarteten Hintergrundprozesses

$PWD 	Aktuelles Arbeitsverzeichnis

$OLDPWD 	Der Wert ist das zuvor besuchte Arbeitsverzeichnis; wird vom Kommando cd gesetzt.

$HOME 	Heimverzeichnis für den Benutzer; Standardwert für cd

$UID 	Die User-ID des Anwenders. Diese Kennung ist in der Datei /etc/passwd dem Benutzernamen zugeordnet.

$PATH 	Suchpfad für die Kommandos (Programme); meistens handelt es sich um eine durch Doppelpunkte getrennte Liste von Verzeichnissen, in denen nach einem Kommando gesucht wird, das ohne Pfadangabe aufgerufen wurde; Standardwerte: PATH=:/bin:/usr/bin

$CDPATH 	Suchpfad für das cd-Kommando

$BASH 	Kompletter Pfadname der aktuellen Shell

$RANDOM 	Pseudo-Zufallszahl zwischen 0 bis 32767

$REPLY 	Bei Menüs (select) enthält REPLY die ausgewählte Nummer.

$SECONDS 	Enthält die Anzahl von Sekunden, die seit dem Start (Login) der aktuellen Shell vergangen ist.

$PROMPT_COMMAND 	Hier kann ein Kommando angegeben werden, das vor jeder Eingabeaufforderung automatisch ausgeführt wird.

$PS1 	Primärer Prompt; Prompt zur Eingabe von Befehlen.

$TZ 	Legt die Zeitzone fest (hierzulande MET = Middle European Time)

### Aritmetische Zeichen
|Zeichen|Bedeutung|Beispiel|
---|---|---|
|+|Addition|add=$((a+b))|
|-|Subtraktion|sub=$((a-b))|
|*|Multiplikation|multi=$((a*b))|
|/|Division(Ganzzahl)|div=$((a/b))|
|%|modulo(Ganzzhlrest von a/b)|mod=$((a%b))|
|**|potenz|pot=$((a**b))|

### Zeichenketten Verarbeitung$
