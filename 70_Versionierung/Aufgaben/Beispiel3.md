# Beispiel mit zwei Branches

Dieses Beispiel baut auf [Beispiel 2](Beispiel2.md) auf und ist in IntelliJ umgesetzt,
da der Vergleich in einer grafischen Oberfläche angenehmer ist.  
Das Beispiel lässt sich auch mit jedem anderen GUI oder CLI Klienten umsetzen.

---

Zuerst legen wir einen neuen *Branch* an. Nennen wir ihn *feature-branch*.  
Dann erweitern wir das Projekt auf diesem neuen Versionspfad,  
indem wir ein Ausrufezeichen an unsere Daten anhängen.

<img src="Bilder/Beispiel3%20-%20new%20branch.jpg" width="800px">

Auf dem neuen Branch: Der neue Pfad ist sichtbar und auch die neue Version (Commit) lässt sich einordnen.  
Mit einem Doppelklick auf veränderte Einträge im Commit-Reiter von intelliJ öffnet sich der Diff-Reiter.  
Hier können wir den Unterschied gut sehen.

<img src="Bilder/Beispiel3%20-%20on%20new%20branch.jpg" width="800px">

Sollten Sie nicht alles sehen, überprüfen Sie, dass kein Filter in der Baumübersicht aktiv ist.

<img src="Bilder/Beispiel3%20-%20new%20branch%20after%20commit.jpg" width="800px">

Anschließend führen wir die Versionen zusammen. Stellen Sie sich vor, dass der *feature-branch* nicht von Ihnen,  
sondern einer Arbeitskolleg:in angelegt wurde. Wir wollen die Änderung in den *master* Branch übernehmen.

Zuerst wechseln wir auf den *master* Branch zurück, dann *mergen* (Vereinigen) wir den *feature-branch* mit *master*.

![](Bilder/Beipsiel3%20-%20merge%20goal.excalidraw.png)

![](Bilder/Beispiel3%20-%20checkout%20master.jpg)

<img src="Bilder/Beispiel3%20-%20merge%20feature%20into%20master.jpg" height="400px">
