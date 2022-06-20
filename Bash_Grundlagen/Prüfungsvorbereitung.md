### a) Was macht folgende Zeile?

     ifconfig | grep "Ether" -c

     Zählt wie oft der Begriff *ether* in der Ausgabe von grep vorkommt.


### b) Was macht folgende Zeile?

     tar -vczf backup.tar.gz /root/

     Komprimiert und archiviert den Inhalt des Ordners `/root/` in der Datei `backup.tar.gz`


### c) Füllen sie eine Datei namen.txt mit folgendem Inhalt (Inhalt copy-paste)

     Otto
     Peter
     Martin
     Christian
     Andrea
     Tim
     Sven
     Heinz
     Bob

### Was macht folgender Befehl?

	cat namen.txt | sort -u

    Gibt die Begriffe in alphabetischer Reihenfolge ohne Duplikate aus



### d) Formulieren sie einen Befehl, welcher aus der Datei /etc/passwd alle Heimverzeichnisse ausschneidet und in einer Datei homes.txt speichert.

cat /etc/passwd | cut -d ':' -f 6 > homes.txt



### e) Formulieren sie eine for-schleife, welche durch die Zahlen 1 bis 10 läuft und das Produkt der Zahlen mit sich selbst ausgibt.

	for z in {1..10};do echo $((z*z)); done



### f) Wie oft laufen folgende cronjobs?

     */10 * * * * <befehl1>
     5 8 * * 0 <befehl2>
     0 10 1 * * <befehl3>

     1: Alle 10 Minuten
2: Sonntags um 8:05 Uhr
3: An jedem 1.Tag im Monat um 10:00 Uhr




### g) Was macht folgender Befehl? (Zum Testen IP-Adresse anpassen und fping installieren!)

     fping -g -c 1 -t250 172.16.6.0/24 2>&1 | grep " 0% " | cut -d " " -f 1

     Enfacher Ping-Sweep des fping-Befehls mit `-g` Option
 



### h) Was macht folgendes Skript?

	#!/bin/bash
	for i in $( ifconfig | grep "inet" | grep -v "127.0.0.1" | cut -d ":" -f 2 | cut -d "." -f 1-3 ); do
	  #echo $i #Zum Testen entkommentieren
	  for k in $(seq 1 255); do
	      #echo $k #Zum Testen entkommentieren
	      fping -c 1 -t250 $i.$k 2>&1 | grep " 0% " | cut -d " " -f 1 >> ips.txt
	  done
	done

    



### i) Was macht folgender Befehl?

     find / -user otto -iname "*bash*" -exec cp {} /data/otto/ \;


### j) Was machen folgende Befehle?

      for ip in $(seq 200 254);do echo 192.168.13.$ip; done > ips.txt
      for ip in $(cat ips.txt);do dig -x $ip | grep $ip >> dns.txt; done