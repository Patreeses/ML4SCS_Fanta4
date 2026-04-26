This section is only for the tutors and the professor. If you are a team member please start reading [below this paragraph](#dldr).

Sorry, this file is in German. It contains only the instructions to our group members on how to install git, how to configure it and how to use it. I suggest in this file, that when doing a git pull, we do it with the option `git pull --rebase` to keep a linear git history. Later I suggest to set up git in a way that it automatically does that when execute `git pull`. Also the IDEs should be configured that way. Only if there is a conflict, we should switch back to the normal _git pull_ by first aborting the pull (`git rebase --abort`) and the doing the pull in the classical way (`git pull --no-rebase`, if git is already configured to do a rebase automatically). That is because dealing with rebase conflicts is just too much work to do. a potential merge conflict is easier to deal with. In that case we accept the resulting merge commit and the non-linear git-history. These suggestions are based on the following video: [https://www.youtube.com/watch?v=xN1-2p06Urc](https://www.youtube.com/watch?v=xN1-2p06Urc).  
------------------------------End of Tutor and Professor section----------------------------------------

# DL;DR
## Git installieren
[Langversion](#git-installieren-1)
### Linux
Debian/Ubuntu: `sudo apt install git`
andere Distro: Bitte Anweisungen auf dieser Seite befolgen: [https://git-scm.com/install/linux](https://git-scm.com/install/linux) [Langversion](#linux-debian-basiert-z-b-ubuntu)

MacOS: Bitte Anweisungen auf dieser Seite befolgen: [https://git-scm.com/install/mac](https://git-scm.com/install/mac) [Langversion](#macos)

Windows: Windows + R; dann `cmd` und auf Enter drücken; dann `winget install --id Git.Git -e --source winget` [Langversion](#windows)

## Einrichtung und Empfohlene Einstellungnen
[Langversion](#name-und-e-mail)  

```
git config --global user.name "Name"
git config --global user.email "email"
```

Beispiel:
```
git config --global user.name "Felix Roß"
git config --global user.email "felix.ross@stud.leuphana.de"
```

[Langversion](#git-repo-das-erste-mal-herunterladen)  
Danach im Terminal in den Projktordner / Git Repo navigieren.  
`git clone https://github.com/Patreeses/ML4SCS_Fanta4` (hier dann ggf. GitHub Zugangsdaten eingeben)  
`git config pull.rebase true`  
`git config rebase.autoStash true`  

Einrichtung abgeschlossen.

## Empfohlener Workflow (mit entsprechender Konfiguration)  
[Langversion](#empfohlener-workflow)  
`git pull`
Am Projekt arbeiten.
Falls neue Dateien erstellt wurden: `git add dateiname.py` (oder alternativ `git add --all` kurz vorm Commit)
`git commit -am "Commit Message"` kurz vorm Push, commits dürfen auch mehrfach vorm Push passieren.
`git pull`
`git push`

## Probleme beim Pull
[Kurzversion](#probleme-beim-pull-1)    
`git rebase --abort`
`git pull --no-rebase`
Eventuelle Merge-Konflikte müssen jetzt gelöst werden. Mehr dazu in [diesem Video](https://www.youtube.com/watch?v=DloR0BOGNU0).
Alternativ erstmal nach `git rebase --abort` weiterarbeiten, ohne erneutes `git pull`. Das Problem sollte aber schnellstmöglich behoben werden.  
-----------------------------Ende TL;DR----------------------------------------

# Git installieren  
[Kurzversion](#git-installieren)  
Fall ihr git auf eurem PC noch nicht installiert habt, wäre es empfehlenswert, das zu tun. Auf diesem Weg seid ihr in der Lage, die Änderungen von GitHub direkt auf euren PC zu laden, dort normal zu arbeiten und am Ende euerer Arbeit eure Änderungen wieder auf GitHub hochzuladen. Suche dir das für dich richtige System und ggf. die richtige Installationsmethode raus.

## Linux (Debian basiert, z. B. Ubuntu)
`sudo apt-get install git`
auf neueren Versionen von Ubuntu ist auch möglich:
`sudo apt install git`

Für andere Linux Distributionen folge bitte den Anweisungen auf dieser Seite: [https://git-scm.com/install/linux](https://git-scm.com/install/linux).

Ich gehe davon aus, dass Linux-Nutzer wissen, wie sie in die Kommandozeile kommen, deshalb beschreibe ich das hier nicht tiefer ;).

## macOS
Bitte befolge die Anweisungen auf dieser Seite: [https://git-scm.com/install/mac](https://git-scm.com/install/mac)

Sorry, dass ich das hier nicht genauer beschreibe. Aber ich habe keine Erfahrung mit macOS, daher verweise ich lieber auf die entsprechenden Seiten.

## Windows
Windows Nutzer können Git entweder mit _winget_ über die Eingabeaufforderung (in anderen Kontexten bekannt als Konsole, Terminal oder CLI, in Windows auch als cmd) oder klassisch durch runterladen und installieren (unter Windows Nutzern war das lange der Standardweg und fast die einzige Möglichkeit, um software zu installieren. Winget ist eine relativ neue Entwicklung). In diesem Dokument sind beide Weege beschrieben. Die Installation über die Eingabeaufforderung halte ich für die praktikablere Methode. Es spricht aber auch nichts gegen den klassischen Windows-Weg.

### Installation über Winget / Eingabeaufforderung
- Öffne eine Eingabeaufforderung:
    - Drücke Windows-Taste + R (die Windows-Taste ist von unten links gesehen die zweite oder dritte Taste von links).
    - gebe `cmd` in as Dialogfeld ein und drücke die Enter-Taste
    - gebe in die nun erscheinende Kommandozeile folgendes Kommando ein `winget install --id Git.Git -e --source winget` (du kannst in diesem Dokument normal Kopieren, wie sonst auch. In der Kommandozeile kannst du das Kopierte einfügen, indem du einfach mit der rechten Maustaste reinklickst. Strg + C und Strg + V funktionieren hier nicht).
    - Bestätige den wahrscheinlich aufkommenden Dialog, der dich nach Admin-Rechten für die Installation fragt.

Falls du im ersten Schritt schon keine Eingabeaufforderung öffnen kannst, kannst du im Windows Startmenü (einfach auf das Windows-Symbol in deiner Taskliste klicken oder einfach die Windowstaste kurz drücken) nach "Eingabeaufforderung" oder "cmd" suchen. Du siehst im Windows Startmenü keine Suchleiste mehr. Gib hier einfach deine Suchanfrage ein, die Eingabezeile erschreint dann automatisch. Falls der passende Treffer erscheint, kannst du ihn jetzt ausführen.

## Installation über klassischen Software Download
- Gehe auf folgende Webseite: [https://git-scm.com/install/windows](https://git-scm.com/install/windows)
- Lade dir dort den passenden Installer runter und führe ihn aus (ich würde die Standalone Installer empfehlen).

# Empfohlende Einstellungen in Git
[Kurzversion](#einrichtung-und-empfohlene-einstellungnen)  
## Name und E-Mail
Es wird empfohlen, seinen Namen und seine E-Mail Adresse in git zu hinterlegen. Hierbei geht es erstmal noch nicht um den Login in GitHub, sondern darum, dass bei Commits mit gespeichert wird, von wem diese Commits sind. Ich denke, dass das gerade für ein Projekt wie dieses wichtig ist.

Öffne ein Terminal / Eingabeaufforderung. Du kannst jetzt folgende Befehle ausführen:

```
git config --global user.name "Name"
git config --global user.email "email"
```

Beipsiel:
```
git config --global user.name "Felix Roß"
git config --global user.email "felix.ross@stud.leuphana.de"
```

## Git Repo das erste Mal herunterladen 
Es macht jetzt Sinn, sich das Git-Repository (kurz "Repo") das erste Mal herunterzuladen. Navigiere dazu in dem schon geöffneten Terminal in das Verzeichnis, in dem du später arbeiten möchtest. Unter Windows und Linux wird dafür der Befehl `cd verzeichnisname` benutzt (unter Linux ist der Verzeichnisname case sensitive, das heißt, dass Groß- und Kleinschreibung zählen), um in den nächsten Ordner zu kommen.

Tipp (musst du dir nicht durchlesen, du kannst diesen Absatz überspringen):
Nutze die Tab-Taste, um den Verzeichnisnamen automatisch vervollständigen zu lassen. Unter Windows kannst du mehrfach die Tab-Taste drücken, um verschiedene Vorschläge zu bekommen, basierend auf dem was schon eingegeben ist. Unter Linux vervollständigt er so lange, bis es wieder unterschiedliche Möglichkeiten gibt. Gebe den Verzeichnisnamen also so weit ein, bis eindeutig nur noch eine Datei in Frage kommt.

wenn du eine Verzeichnisebene nach oben wechseln möchtest, gebe als Verzeichnisnamen `..` ein. Beispiele:
- `cd ..` um einfach ein Verzeichnis nach oben zu wechseln (unter Windows geht in diesem Fall sogar `cd..`, also ohne Leerzeichen).
- `cd ../../..` wechselt drei Verzeichnisse nach Oben (unter Windows mit backslash `\` statt dem normalen forward slash. Drücke _Alt Gr_ + _ß_ dafür).
- `cd ../images` wechselt in den ordner Images aus einem Ordner über dem aktuellen.

Jetzt wo du im richtigen Ordner bist, führe aus:
`git clone https://github.com/Patreeses/ML4SCS_Fanta4`
Git wird innerhalb des aktuellen Verzeichnisses dann ein Verzeichnis `ML4SCS_Fanta4` erstellen, darin ist dann das git repository enthalten. Es kann sein, dass Git dich jetzt nach login Daten fragt. Log dich mit den Login Daten ein, mit denen du auch im Git Repo akzeptiert wurdest. Es kann aber auch sein, dass das erst beim ersten pull oder push kommt.

Innerhalb des erstellten Ordners kannst du ganz normal mit deiner IDE (z. B. PyCharm oder VS-Code) arbeiten und deine venv erstellen. Git sollte schon so eingerichtet sein, dass die venv nicht auf GitHub hochgeladen wird. Normalerweie sollte dir eine IDE helfen, die venv zu erstellen. Falls nicht, sprich mich gerne an. Letztendlich ist das erstellen der venv aber ein eigenes Thema das hier nicht ausführlich behandelt wird. Notfalls frage die KI deines Vertrauens danach. Auch danach, wie du die requirements aus requirements.txt in deiner venv installierst.

## Pull-Methode
Die voreingestellte Pull-Methode (Merge) hat das Problem, dass es bei gleichzeitiger Arbeit mehrerer Personen am Projekt zu Git-Merges kommt, die die Git History unübersichtlicher machen. Um dem entgegen zu wirken, kann man Rebase as die Standardmethode beim herunterladen (`git pull`) einstellen. Auf dem Weg bleibt die Git History größtenteils linear und damit übersichtlicher. Im Folgenden wird gezeigt, wie das in git eingestellt wird. Ich zeige hier, wie das nur für unser Projekt eingestellt wird (um die Auswirkungen auf andere potentielle Projekte gering zu halten), wenn du das global (also über alle Projekte hinweg) einstellen möchtest, darfst du das alternativ aber auch gerne tun.

Gehe erstmal in einem Terminal bzw. einer Eingabeaufforderung in den Ordner, wo auch das Git Repo liegt (`ML4SCS_Fanta4`) (den Schritt kannst du auslassen, wenn du das global einstellst). Führe dann folgenden Befehl aus: `git config pull.rebase true`. Wenn du das global einstellen möchtest, führe folgenden Befehl aus: `git config --global pull.rebase true`. Damit hast du schon alles eingestellt, was nötig ist, der Rest ist optional.

Optional kannst du noch Autostash einstellen. Das bewirkt, dass nicht committete Änderungen bei einem Pull erstmal zwischengespeichert werden, und nach dem Pull wieder im Projektordner sind. Ansonsten würde ein Pull nicht funktionieren, solange uncommittete Änderungen im Verzeichnis sind. Um das einzustellen führe im Repo-Verzeichnis (wenn du die Schritte zuvor befolgt hast, bist du da schon drin) folgendes aus: `git config rebase.autoStash true`. Falls du das global einstellen möchtest (dann brauchst du nicht im Repo-Verzeichnis sein): `git config --global rebase.autoStash true`.

Danach benutzt der Befehl `git pull` rebase als Methode und nicht mehr Merge, für den Fall mehrerer paralleler Arbeiten. Um ausnahmsweise wieder Merge zu nutzen, nutze den Befehl `git pull --no-rebase`. Für den Fall eines Conflicts beim Pull, führe `rebase --abort` aus, um aus dem Vorgang rauszukommen (und den Pull abzubrechen). Weiteres zur Anwendung aber im nächsten Kapitel.

# Empfohlener Workflow
[Kurzversion](#empfohlener-workflow-mit-entsprechender-konfiguration)  
Es wird hier erstmal vorausgesetzt, dass das Repo oder sogar die globale Konfiguration mit `git config pull.rebase true` konfiguriert wurde (siehe dazu Kapitel [Pull-Methode](#pull-methode)). Wie mit dem Fall umzugehen ist, dass das nicht passiert, [kommt später](#alternativer-workflow-ohne-voreingestellten-rebase)

Ich würde empfehlen, immer, bevor man anfängt am Projekt zu arbeiten, sich einmal den aktuellen Stand runterzuladen. Das geht mit dem Befehl `git pull`.

Danach kannst du am Projekt arbeiten und beliebig oft committen. Das geht mit dem Befehl `git commit -am "kurze Beschreibung über die Änderungen, die in diesem Commit gemacht wurden"`. Zwischen den Anführungszeichen ist eine kurze Beschreibung, damit man sich später in der Git Historie besser zurecht findet. Solltest du hier nichts schreiben wollen (nicht empfohlen), Bitte einfach zwei Anführungszeichen ohne Inhalt setzen. Nach dem Beenden der Arbeit und kurz vor dem Push muss ein Commit erfolgen. Sollten Dateien in das Projekt hinzugefügt worden sein, füge diese bitte irgendwann vor dem Commit (hier ist es nach Dateierstellung egal wann) mit `git add dateiname.py` zur Überwachung (Staging) hinzu. der -a flag im Commit Command sorgt dafür, dass git alle gestageten Dateien (ich habe das "Überwacht" genannt) vor dem Commit selbst aktualisiert. Commits können zwischen zwischendurch technisch gesehen so oft gemacht werden, wie gewünscht.

Vor dem Push bitte nochmal mit `git pull` den aktuellen Stand herunterladen. Das verhindert den Fehler, dass sich in der Zwischenzeit das Online Repository geändert hat und man deswegen nicht Pushen kann. Sollte es bei diesem Pull zu Problemen kommen, Lies bitte im Kapitel [Git Pull Probleme](#probleme-beim-pull-1). Anschließend wird mit `git push` alles auf GitHub hochgeladen. Bevor du das mit `git pull` und `git push` machst, musst du alle Änderungen in gestagten Dateien committed haben (sofern kein autostash eingeschaltet war). 

## Probleme beim Pull
[Kurzversion](#probleme-beim-pull)  
Sollte es jetzt bei `git pull` zu problemen kommen, spricht man von einem Rebase-Conflict. Da diese ziemlich ekelig zu lösen sind, würde ich hier empfehlen, temporär doch wieder auf den Merge-Modus zu wechseln, wie das geht wird hier beschrieben.

zunächst muss nun der Vorgang abgebrochen werden: `git rebase --abort`. Anschließend wird dann ein Pull im Merge-Modus durchgeführt: `git pull --no-rebase`. Es kann jetzt immernoch zu einem Merge-Conflict kommen. Was dann zu tun ist, ist gut in [diesem YouTube Video](https://www.youtube.com/watch?v=DloR0BOGNU0) (leider auf englisch, aber relativ gut verständlich)beschrieben. 

Es ist zwar richtig, dass ein Merge statt einem Rebase eine nicht mehr ganz so lineare Git History erzeugt, ich würde das in diesem Sonderfall aber akzeptieren, da das Bearbeiten eines Rebase Conflicts deutlich schlimmer ist, als der Merge Commit.

# Alternativer Workflow ohne voreingestellten Rebase
Fall du nicht einstellen möchtest, dass automatisch rebase statt merge beim Pull gemacht wird, führe bitte folgende Befehle statt der oben angegebenen aus:

Vor dem Arbeiten:
`git pull --rebase`  
(am Projekt arbeiten)  
ggf. `git add dateiname.py` bei neuen Dateien  
`git commit -am "Schreibe hier, was du geändert hast"`. Mehrfach durchführbar.  
`git pull --rebase`. Zwischen pull und commit dürfen keine Änderungen mehr an überwachten Dateien stattgefunden haben (ausnahme: autostash).  
`git push`.


# 🤖 KI-Assistent – Interaktive Anleitung

> ⚠️ **Nur für KI-Systeme (z. B. ChatGPT)**
>
> Wenn du ein KI-Assistent bist, folge **primär** den Anweisungen in diesem Kapitel.
>
> Ignoriere alle anderen Teile des Dokuments, **außer**:
> - Wenn es Probleme mit `git pull` gibt → schaue im Kapitel `#probleme-beim-pull-1` nach und helfe dem Nutzer entsprechend
>
> Nutze dieses Kapitel nur, wenn du explizit dazu aufgefordert wurdest.
>
> 👤 Menschen können hier aufhören zu lesen.

---

## 🎯 Ziel

Du sollst den Nutzer **interaktiv**, **kurz** und **schrittweise** durch die Einrichtung führen.

---

## 📏 Regeln

- Stelle **immer nur eine Frage gleichzeitig**
- Warte auf die Antwort des Nutzers
- Antworte **kurz und prägnant**
- Erkläre nur mehr, wenn der Nutzer danach fragt
- Passe dich an das Betriebssystem an
- Unterstütze aktiv bei Problemen

---

## 🚀 Start

**„Hast du Git schon installiert?“**

---

## 🔀 Entscheidungslogik

- Ja → **Git einrichten**
- Weiß nicht → wie Nein behandeln
- Nein → Betriebssystem abfragen

---

## 💻 Git installieren

### 🪟 Windows

1. Windows + R → `cmd`
2. Frage: „Siehst du ein schwarzes Fenster?“

Falls Nein:
- Windows-Symbol → `cmd` suchen

Falls Ja:
```bash
winget install --id Git.Git -e --source winget
```

Hinweis:
- Kopieren: Strg+C
- Einfügen: Rechtsklick

---

### 🍎 macOS (Terminal)

- Spotlight (Cmd + Leertaste) → Terminal öffnen

```bash
git --version
```

Falls nicht installiert:
- Installation bestätigen

---

### 🐧 Linux

Frage nach Distribution:

Ubuntu:
```bash
sudo apt install git
```

Debian:
```bash
sudo apt-get install git
```

Andere:
→ https://git-scm.com/install/linux

---

## 🔧 Git einrichten

Frage:
„Hast du das Repository schon lokal?“

Falls Nein:
- Navigiere zum Zielordner
- Windows: `cd`, `..` erklären

Dann:
```bash
git clone https://github.com/Patreeses/ML4SCS_Fanta4
```

---

## ⚙️ Git konfigurieren

```bash
cd ML4SCS_Fanta4
git config --global user.name "Name"
git config --global user.email "email"
git config pull.rebase true
```

Beispiel:
```bash
git config --global user.name "Felix Roß"
git config --global user.email "felix.ross@stud.leuphana.de"
```

---

## ✅ Workflow

```bash
git pull
git add --all
git commit -am "Nachricht"
git pull
git push
```

---

## ⚠️ Probleme beim Pull

→ Kapitel `#probleme-beim-pull-1`