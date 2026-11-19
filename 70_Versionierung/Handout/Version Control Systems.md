# Version Control Systems (VCS)

In diesem Handout gehen wir von [Git](https://git-scm.com/docs) als VCS aus.   
Git ist nicht das einzige VCS, aber in der Welt der Softwareentwicklung das,   
welches am meisten verbreitet ist.

[Gutes Online-Tutorial mit visuellen Erklärungen und Übungen](https://learngitbranching.js.org/) - Tipp:  
als Erstes das Kommando ``flip`` benutzen, um den Commit-Tree so darzustellen, wie im Unterricht.  
([Sandbox Modus](https://learngitbranching.js.org/?NODEMO=&locale=en_EN) ohne Übungsaufgaben)

[Gutes Tutorial in Textform](https://de.w3docs.com/learn-git/introduction4)

## Grundlegende Konzepte

Eine **Version** in einem VCS speichert die Änderungen im Vergleich zur vorherigen Version.  
Diese Änderungen beziehen sich nicht nur auf eine einzelne Datei, sondern auf den gesamten Projektzustand.  
Solche Versionen werden als **Commits** bezeichnet und bilden zusammen die **Commit-Historie**.  
Ein Commit können Sie auch als Speicherpunkt verstehen.

Auf Basis jeder gespeicherten Version kann weitergearbeitet werden.  
Dies geschieht über sogenannte **Branches** (Verzweigungen), die parallele Entwicklungsstände ermöglichen.  
Ein Branch ist eigentlich nur ein Bezeichner, hinter dem ein spezieller Commit steht,  
der **Current Head** (aktueller Kopf des Zweigs). Entwickelt sich ein Versionszweig weiter,  
verschiebt man also eigentlich nur diesen Bezeichner entlang der Commit-Historie.

Statt mit einzelnen Dateien zu arbeiten, wird in **Repositories** organisiert.  
Diese enthalten das gesamte Projekt, also alle Branches mit deren Commit-Historien.

Repositories existieren in zwei Formen:

- **Remote repositories** dienen der Zentralisierung und gemeinsamen Nutzung von Versionen.
- **Locale repositories** ermöglichen die verteilte Arbeit und enthalten vollständige Kopien des Projekts.   
Jeder Nutzer hat ein eigenes lokales Repository. Dieses bildet eine lokale Kopie des Remote repository.

Als **Head** (Kopf einer Version) bezeichnen wir den Commit, der angibt auf welchem Stand ein **Branch** ist.  
Oder anders ausgedrückt: Ein **Branch** ist eigentlich nur die Referenz zu einem ganz bestimmten Commit,  
und damit zu einer bestimmten Version.

### Beispiel Local repository:

"New Feature" ist eine neue Verzweigung der Versionshistorie.  
Die Zweige "Main" und "New Feature" bezeichnen wir in diesem Moment als **parallele Zweige**.  
Denn es sind zwei parallele Versionen unseres Projekts.  
Beachten Sie auch, dass die Commits 1 bis 3 technisch gesehen zu beiden Zweigen gehören.  

<img src="./Bilder/repository%20and%20branch%20overview.excalidraw.png" width="50%" alt="Repository Beispiel zeigt mehrere Commits und einen davon abgehenden Branch">

### Beispiel mit Remote repository:

Das Repository, das wir als unseren **"Remote"** bezeichnen, weiß hier noch nichts von unserem "New Feature".  
Der neue **Branch** muss noch hochgeladen ("push") werden.  
Das **"Remote"** stellt eine Kopie von unserem **Local Repository** dar.

<img src="./Bilder/local%20remote%20overview.excalidraw.png" width="50%" alt="Repository Beispiel zeigt jetzt auch den Remote, wo aber der neue Branch fehlt">

---

## Funktionen und Vorteile

Versionskontrollsysteme ermöglichen die Verwaltung von **Varianten eines Projekts**.  
Jede Änderung wird in einer lokalen Historie festgehalten. Dadurch ist es jederzeit möglich,  
zu einem früheren Stand zurückzukehren oder gezielt Änderungen rückgängig zu machen.  
Fehler lassen sich somit einfacher korrigieren.

Ein großer Vorteil liegt in der **Kollaboration und Synchronisation**.  
Mehrere Personen können gleichzeitig an einem Projekt arbeiten und ihre Änderungen zusammenführen.  
Dabei entsteht eine gemeinsame, nachvollziehbare Historie aller Beiträge.

Durch die Historie entstehen automatisch **Backups**.  
Jeder gespeicherte Stand ist dauerhaft verfügbar und kann wiederhergestellt werden.  
Ein separater Backup-Prozess ist dadurch oft nicht mehr notwendig.

Dadurch entsteht **mehr Sichtbarkeit**:  
Die tatsächlichen Veränderungen sind klar ersichtlich,  
sowie wann, welche und von wem diese vorgenommen wurden.

Die Arbeit mit einem VCS erhöht die **Sicherheit**.  
Änderungen gehen nicht verloren und bleiben strukturiert gespeichert.  
Selbst bei Fehlern oder technischen Problemen ist der Zugriff auf frühere Versionen gewährleistet.

Ein weiterer Vorteil ist die **verbesserte Kommunikation** im Team.  
Fortschritte und Änderungen sind transparent,  
wodurch sich Fehler schneller erkennen und beheben lassen. 
Alle Beteiligten haben denselben Informationsstand.  

Die **automatisierte Synchronisation** erleichtert zusätzlich die Zusammenarbeit.  
Systeme warnen vor Konflikten zwischen Änderungen, bieten Vergleichsfunktionen  
und ermöglichen das parallele Arbeiten an unterschiedlichen Versionen eines Projekts.

---

## Einrichten

1. Wir benötigen einen Git Client, ein Programm das mit dem Protokoll von Git den Datenaustausch regelt.
   * Auf der [offiziellen Seite](https://git-scm.com/tools) von Git gibt es mehrere CLI Tools oder solche mit grafischer Oberfläche.
   * Mit den gängigen IDEs ist oft ein Git Client vorinstalliert.
2. Zum Speichern des Remote repository eignen sich Anbieter wie [Github](https://github.com/)
oder [Gitlab](https://gitlab.com/). Git kann auch selbst gehostet werden.
3. Zum Erstellen der Verbindung zwischen dem Local repository und dem Remote repository müssen wir uns  
bei unserem lokalen Git Client anmelden und diesen Account auf der Platform von unserem Remote repository   
die nötigen berechtigungen geben. Folgen Sie hierzu den Anweisungen auf Github/Gitlab.  
I.d.R. stehen uns die Optionen SSH oder HTTPS zur verfügung.  
Für Mac und Linux bietet sich SSH an, auf Windows ist die Anmeldung über HTTPS oft leichter.
4. Mit der Berechtigung muss nun nur noch die Verbindung hergestellt werden.
Folgen Sie den Schritten ihres lokalen Git Clients.
   * Entweder laden Sie ein gerade erstelltes, lokales Repository hoch.  
   Dadurch wird es zum Remote repository und die Verknüpfung ist entstanden.
   * Oder Sie laden von einem existierenden Remote repository Ihr Local repository herunter.  
   Diesen Vorgang nennen wir "einen **Clone** erstellen."
5. Fertig. Nun können Sie Branches erstellen hoch oder herunterladen. (**Push** oder **Pull**)

---

## FAQ

Überschreibt man nicht schnell Arbeit von jemandem?

- Nein, Git löst die simplen Konflikte zuverlässig, z.B. zwischen Dateien, die nichts miteinader zu tun haben.

Warum löst Git nicht alle Konflikte einfach selbst?

- Nicht alle Unterschiede sind eindeutig lösbar. Manchmal müssen die Autoren entscheiden, ob die eine, die andere oder
  beide Änderungen übernommen werden sollen.