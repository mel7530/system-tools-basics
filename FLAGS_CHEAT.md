# Flags-Cheat

Flags = Optionen, die das Verhalten eines Befehls ändern  
**Befehl = was, Flag = wie**

---

## grep (Text suchen)

-n    Zeilennummern anzeigen  
      grep -n "while" datei.py

-r    Rekursiv (alle Unterordner)  
      grep -r "while" .

-i    Groß-/Kleinschreibung ignorieren  
      grep -i "while" datei.py

---

## fd (Dateien finden)

-   keine Flags nötig-  
    fd name

-x    Befehl für jede gefundene Datei ausführen  
      fd py -x grep -n "while"

---

## find (klassisch)

-name     exakter Name  
          find . -name "datei.py"

-iname    Name ohne Beachtung von Groß/Klein  
          find . -iname "*loop*"

---

## open (macOS)

-a    Bestimmte App verwenden  
      open -a Safari

-n    Neues Fenster / neue Instanz  
      open -na Safari

---

## git (Basics)

-m    Commit-Nachricht  
      git commit -m "message"


