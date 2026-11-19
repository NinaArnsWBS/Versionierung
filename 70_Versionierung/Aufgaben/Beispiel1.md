# Beispiel einer einfachen Versionierung

Dieses Beispiel stellt den Verlauf in der Git CLI dar.  
Die Schritte sollten sich genauso gut in einem Klienten mit grafischer Oberfläche umsetzen lassen.

---

In einem leeren ordner `Beispiel1`:
Zunächst testen wir, ob der Git CLI Klient installiert ist. Dann initialisieren wir ein **Local repository**

```
$> git -v
    git version 2.45.1.windows.1

$> git init
    Initialized empty Git repository in C:/Users/max.muster/.../Beispiel1/.git/
```

Nun erstellen wir `Daten.txt`, geben `Hello World` dort ein und speichern die Datei.
Dann kehren wir zum Terminal zurück.

```
$> git status
    On branch master
    No commits yet
    Untracked files:
      (use "git add <file>..." to include in what will be committed)
            Daten.txt
    nothing added to commit but untracked files present (use "git add" to track)
```

Mit dem `status` Befehl lesen wir aus, wie der Klient unseren Arbeitsstand wahrnimmt.  
Wir können die neue Datei in unserem Projekt nun für einen Commit markieren  
und dann den Commit (eine neue Version)
des Projekts erstellen.

```
$> git add .\Daten.txt
$> git status
    On branch master
    No commits yet
    Changes to be committed:
      (use "git rm --cached <file>..." to unstage)
            new file:   Daten.txt

$> git commit -m "added Hello World msg to Daten.txt"
    [master (root-commit) e2f3eb7] added Hello World msg to Daten.txt
     1 file changed, 1 insertion(+)
     create mode 100644 Daten.txt

$> git status
    On branch master
    nothing to commit, working tree clean
```

Die erste Version unserer Arbeit ist abgelegt (Commit erstellt).  
Alle Änderungen bis zum nächsten Commit werden nun relativ zu diesem Stand gesehen.

Wir Übersetzen die Zeile unserer Datei von `Hello World` zu `Hallo Welt`, speichern und kehren zu Git zurück:

```
$> git status
    On branch master
    Changes not staged for commit:
      (use "git add <file>..." to update what will be committed)
      (use "git restore <file>..." to discard changes in working directory)
            modified:   Daten.txt
    
    no changes added to commit (use "git add" and/or "git commit -a")

$> git diff
    diff --git a/Daten.txt b/Daten.txt
    index 5e1c309..a92550c 100644
    --- a/Daten.txt
    +++ b/Daten.txt
    @@ -1 +1 @@
    -Hello World
    \ No newline at end of file
    +Hallo Welt
    \ No newline at end of file

$> git add .\Daten.txt
$> git commit -m "changed greeting to german"
    [master 62bbb5b] changed greeting to german
     1 file changed, 1 insertion(+), 1 deletion(-)

$> git status
    On branch master
    nothing to commit, working tree clean
```

Jetzt haben wir zwei Versionen: Die erste auf englisch und die neue auf deutsch.
Wir können alle bisherigen Commits einsehen.  
Hier sehen wir auch, dass unser lokaler **Branch** "master" auf dem Stand der neusten Version ist.

Hinweis: "git log"-Befehl durch Drücken der Taste Q verlassen.

```
$> git log
    commit 62bbb5b44293d848a8a2b0868c2ab45ecb636bda (HEAD -> master)
    Author: max.muster <max.muster@wbstraining.de>
    Date:   ...
    
        changed greeting to german

    commit e2f3eb72e31c1fb98a8ecab04e1d3987d42cc98f
    Author: max.muster <max.muster@wbstraining.de>
    Date:   ...
    
        added Hello World msg to Daten.txt
```

Nun wollen wir den Zustand unserer Datei vom ersten Commit wiederherstellen.  
Dafür kopieren wir uns den einzigartigen SHA Wert des Commits, der uns interessiert, also der erste Commit.  
Dann nutzen wir `checkout` mit dem SHA und der Datei, die wir von Dort wiederhaben wollen.

```
$> git checkout e2f3eb72e31c1fb98a8ecab04e1d3987d42cc98f .\Daten.txt
    Updated 1 path from b45f08b
    
$> git status
    On branch master
    Changes to be committed:
      (use "git restore --staged <file>..." to unstage)
            modified:   Daten.txt
```

Der `diff` Befehl zeigt standardmäßig nur Dateien, die noch nicht mit `add` für einen Commit vorbereitet wurden.  
Da `checkout` aber die alte Version automatisch mit `add` vorbereitet, müssen wir `diff` sagen,  
dass wir auch 
vorbereitete Unterschiede ("staged files") noch einmal ansehen wollen:

```
$> git diff --staged
    diff --git a/Daten.txt b/Daten.txt
    index a92550c..5e1c309 100644
    --- a/Daten.txt
    +++ b/Daten.txt
    @@ -1 +1 @@
    -Hallo Welt
    \ No newline at end of file
    +Hello World
    \ No newline at end of file
```

Und auf zur neuen Version: Diese ist in unserem Fall inhaltlich identisch zu unserem ersten Commit.  
Aber das muss natürlich nicht immer so sein. Stellen Sie sich vor, es gäbe viel mehr Dateien  
oder nach dem Zurücksetzen hätten wir noch kleine Änderungen vorgenommen.

```
$> git commit -m "return to englisch version"
    [master 150ee27] return to englisch version
     1 file changed, 1 insertion(+), 1 deletion(-)

$> git status
    On branch master
    nothing to commit, working tree clean

$> git log
    commit 150ee27c41089699751108548920ea56177ca97c (HEAD -> master)
    Author: max.muster <max.muster@wbstraining.de>
    Date:   ...
    
        return to englisch version
    
    commit 62bbb5b44293d848a8a2b0868c2ab45ecb636bda
    Author: max.muster <max.muster@wbstraining.de>
    Date:   ...
    
        changed greeting to german
    
    commit e2f3eb72e31c1fb98a8ecab04e1d3987d42cc98f
    Author: max.muster <max.muster@wbstraining.de>
    Date:   ...
    
        added Hello World msg to Daten.txt
```