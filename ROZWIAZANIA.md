# Rozwiązania – Lab 02: Version control system – Git

## Co jest rozwiązaniem którego zadania

| Zadanie | Rozwiązanie |
|---|---|
| 1. learngitbranching | 11 poziomów rozwiązanych na learngitbranching.js.org – komendy niżej |
| 2. Konto na GitHubie | konto `franko9184-afk` |
| 3. Nowe repozytorium | to repozytorium `hello-git`: opis, plik `README.md` i licencja MIT (plik `LICENSE`) |
| 4. Konfiguracja Gita | komendy `git config` – niżej |
| 5. Klonowanie repozytorium | `git clone` – niżej |
| 6. Plik w repozytorium | plik `hello.txt` (commit „Create hello.txt”) |
| 7. Edycja README w przeglądarce | plik `README.md` (commit „Update README.md”) |
| 8. `cat` i `git pull` | komendy i odpowiedź na pytanie – niżej |
| 9. Pull request do repozytorium prowadzącego | w repozytorium prowadzącego, gałąź `franko9184-afk` |
| Praca domowa | odpowiedź o `.gitignore` – niżej |

## Zadanie 1 – learngitbranching

Main: Introduction Sequence

| Poziom | Komendy |
|---|---|
| Introduction to Git Commits | `git commit; git commit` |
| Branching in Git | `git branch bugFix; git checkout bugFix` |
| Merging in Git | `git checkout -b bugFix; git commit; git checkout main; git commit; git merge bugFix` |
| Rebase Introduction | `git checkout -b bugFix; git commit; git checkout main; git commit; git checkout bugFix; git rebase main` |

Remote: Push & Pull – Git Remotes

| Poziom | Komendy |
|---|---|
| Clone Intro | `git clone` |
| Remote Branches | `git commit; git checkout o/main; git commit` |
| Git Fetchin' | `git fetch` |
| Git Pullin' | `git pull` |
| Faking Teamwork | `git clone; git fakeTeamwork 2; git commit; git pull` |
| Git Pushin' | `git commit; git commit; git push` |
| Locked Main | `git checkout -b feature; git push origin feature; git branch -f main o/main` |

## Zadanie 4 – konfiguracja Gita

```
git config --global user.name "Imię Nazwisko"
git config --global user.email "email-z-konta-github"
git config -l
```

## Zadanie 5 – klonowanie repozytorium

```
git clone https://github.com/franko9184-afk/hello-git.git
cd hello-git
```

## Zadanie 6 – dodanie pliku do repozytorium

```
echo "Hello git" > hello.txt
git status
git add -A
git commit -m "Create hello.txt"
git push
```

Przy `git push` zamiast hasła do GitHuba podaje się personal access token.

## Zadanie 7 – edycja README.md

Treść pliku `README.md` po edycji w edytorze na GitHubie:

```markdown
# hello-git
Example repository for learning how to use git.

# Credits
The repository was created during a course on PUT.
```

## Zadanie 8 – `cat` i `git pull`

```
cat README.md
git pull
cat README.md
```

**Dlaczego lokalny plik nie zawiera wprowadzonych zmian?**
README został zmieniony tylko w zdalnym repozytorium na GitHubie. Lokalna kopia repozytorium nie synchronizuje się automatycznie, więc zmiany trzeba pobrać poleceniem `git pull` (które wykonuje `git fetch` i scala pobrane zmiany z lokalną gałęzią).

## Zadanie 9 – pull request do repozytorium prowadzącego

Repozytorium prowadzącego: https://github.com/kamilmlodzikowski/TASFRS-Git

1. Issue w repozytorium prowadzącego o tytule: `username: franko9184-afk`
2. Po nadaniu dostępu przez prowadzącego:

```
git clone https://github.com/kamilmlodzikowski/TASFRS-Git.git
cd TASFRS-Git
git checkout -b franko9184-afk
mkdir franko9184-afk
echo "United we stand, divided we fall!" > franko9184-afk/INICJALY.txt
git add -A
git commit -m "Add franko9184-afk directory"
git push -u origin franko9184-afk
```

3. Pull request z gałęzi `franko9184-afk` do gałęzi `main` w interfejsie GitHuba.

## Praca domowa – do czego służy plik `.gitignore`?

Plik `.gitignore` zawiera listę wzorców plików i katalogów, których Git ma nie śledzić. Pasujące pliki nie pojawiają się w `git status` jako nieśledzone i nie są dodawane do commitów przez `git add -A`. Wpisuje się tam np. pliki wynikowe kompilacji, katalogi zależności (`node_modules/`), cache (`__pycache__/`), ustawienia IDE (`.idea/`, `.vscode/`) oraz pliki z hasłami i kluczami (`.env`). `.gitignore` nie działa na pliki, które Git już śledzi – takie pliki trzeba najpierw usunąć z indeksu poleceniem `git rm --cached`.
