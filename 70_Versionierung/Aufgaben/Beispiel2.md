# Beispiel zum Erstellen einer Gitignore

Dieses Beispiel baut auf [Beispiel 1](Beispiel1.md) auf
und ist in Vorbereitung auf [Beispiel 3](Beispiel3.md) diesmal in IntelliJ umgesetzt.  
Das Beispiel lässt sich auch mit jedem anderen
GUI oder CLI Klienten umsetzen.

---

## Konzept

Eine Gitignore ist eine Konfigurationsdatei, die dem Git Klienten sagt, dass bestimmte Dateien vom VCS ignoriert 
werden sollen.  
Normalerweise sind das weitere Konfigurationen im Projekt, die etwa für jeden Nutzer anders sind,
oder auch Credentials,  
die besser nicht geteilt oder Versioniert werden.

---

## Beispiel

In IntelliJ öffnen wir den Ordner der unser *.git* Verzeichnis und die *Daten.txt* enthält.  
(``≡``>``File``>``Open...``)
IntelliJ erstellt den Projektkonfigurationsordner *.idea*.  
Darin ist bereits die erste Gitignore enthalten.

<img src="Bilder/Beispiel2%20-%20default%20gitignore.jpg" height="300px">

So sehen wir, dass etwa *workspace.xml* standardmäßig aus der Versionierung ausgeschlossen wird.  
Der *Commit* Reiter in IntelliJ bietet uns eine Übersicht, die der von ``git status`` ähnelt.

<img src="Bilder/Beispiel2%20-%20commit%20preview.jpg" height="300px">

Wir könnten zusätzlich eine eigene Gitignore anlegen.

<img src="Bilder/Beispiel2%20-%20own%20gitignore.jpg" height="300px">
<br/>
<img src="Bilder/Beispiel2%20-%20own%20gitignore%20commit%20tab.jpg" height="300px">

Weiterhin sehen wir, dass die Gitignore einfach eine Datei ist. D.h. sie wird selbst einfach mit versioniert.  
Dann wollen wir mal:

<img src="Bilder/Beispiel2%20-%20commit%20all.jpg" height="500px">