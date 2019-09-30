# Git

VCS ... Version Contol System (Versionierungssystem)

## Probleme / Anforderungen

- Die Codebasis muss regelmäßig gesichert werden.
- Der Entwickler möchte Zugriff auf ältere Versionen seines Programms haben.
- Meistens werden Softwareprodukte in Teams erstellt; jedes Teammitglied braucht Zugriff auf den Sourcecode
- Teammmitglieder arbeiten oft gleichzeitig an den selben Sourcecode-Files. Sämtliche Änderungen müssen in die Codebasis eingepflegt werden.
- Separates Entwickeln von neuen Features, bis diese fehlerfrei sind und anschließendes Einfügen dieser neuen Funktionen in die Codebasis

## Alternativen

Sind ungenügend:

- regelmäßiges zippen der Codebasis und sichern
- zur Verfügung stellen der Codebasis auf einem File-Server und /oder auf der Dropbox (oder vergleichbare Dienste)

## Aufbau

- zentrale VCS zB Subversion
- dezentrale VCS zB Git

Provider: GitHub, Bitbucket, Gitlab


## Anwendungsfälle

### Erstellen eines Projekts

#### Leeres Projekt aus Git-Repo clonen


```
git remote add origin https://github.com/htl-leonding/my-project.git
git push -u origin master
```

#### Bereits bestehendes Projekt ins Git-Repo commiten

```
echo "# delete-me-please" >> README.md
git init
git add README.md
git commit -m "first commit"
git remote add origin https://github.com/htl-leonding/my-project.git
git push -u origin master
```

### Ein Projekt aus dem Repos downloaden (clonen)

```
git clone <link>
git clone https://github.com/htl-leonding/1920-4ahitm-itp.git
```

### Neue und/oder geänderte Dateien ins das Repo einpflegen

#### Dateien in die Staging Area einpflegen

```
git add <filename.txt>
git add git.md

git add -A
```
-A ... all changes


#### Dateien aus der Staging Area entfernen

```
git reset <filename.txt>
git reset git.md

git reset -A
```
-A ... all changes

#### Dateien in das local-repo einpflegen

```
git commit -m "kommentar"
```

#### Dateien aus dem local-repo entfernen

```
git rm <filename>
git rm git.md
```

#### Dateien in das remote-repo einpflegen

```
git push -u origin <branch name>
git push -u origin master
```

-u ... Speichert origin und branch name damit man später nur 
```
git push
```
machen muss

#### Dateien aus dem remote-repo entfernen

```
git rm <filename>
git rm git.md
```

### Status des Git-Working-Directories ansehen

```
git status
```

### Pretty Printing für Git-Logs

<https://stackoverflow.com/questions/1057564/pretty-git-branch-graphs>

ev. mit Verwendung von .gitconfig

```
git log --all --decorate --oneline --graph
```

### Zweige für eigene Features erstellen

```
git branch <branch name>
git branch login
```

### Branch wechseln

```
git checkout <branch name>
git checkout login
```

In einem Zweig Daten ändern und anschließend im anderen Zweig Daten ändern und beide Änderungen commiten / pushen

```
git add git.md
git commit -m "updated git.md"
git push origin master

git checkout login

git add login.js
git commit -m "fixed bug"

git push origin login
```

### Branch mergen

```
git merge <source branch>

git merge <source branch> <target branch>
```

Login branch in master branch mergen
Man befindet sich im master branch

```
git merge login
```

oder

```
git merge login master
```

### Pull requests durchführen

- Jemand besitzt ein Repo
- Ein anderer cloned dieses Repo und möchte etwas im Original Repo ändern
- Er/Sie führt einen Pull Request durch

```
git clone https://github.com/htl-leonding/1920-4ahitm-itp.git

git add git.md
...
git push https://github.com/htl-leonding/1920-4ahitm-itp.git master

git request-pull <start> <url>
git request-pull login01 https://github.com/htl-leonding/1920-4ahitm-itp.git
```

### Commits taggen

Szenario: Die einzelnen Releases (zB bei Auslieferung an den Kunden) sollen getagged werden

Begriff der Baseline

### Einen Release-Eintrag im Github erstellen (inkl. Doku)

### Verwerfen der lokalen Änderungen

Was bedeutet `stash`