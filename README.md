# Instal·lar git a Windows

* Descarregar el programa ```git```.
https://github.com/git-for-windows/git/releases/download/v2.39.1.windows.1/Git-2.39.1-64-bit.exe

* Pàgina web oficial de GitHub (https://github.com)


Crear la carpeta contenidora del nostre projecte.
Per tal de unificar la nostra explicació, crearem una carpeta que anomenarem pardo-act01, i serà la que farem servir per guardar i centralitzar el projecte o repositori pardo-act01. En el meu cas, la crearé dins de la unitat D: del meu portatil.

Per fer-ho executarem les següents comandes.
```sh
~$ mkdir pardo-act01
~$ mkdir pardo-act01
~$ cd pardo-act01
~/pardo-act01$ pwd
\d\pardo-act01
```

Un cop ja siguem dins de la carpeta que acabem de crear podem provar d’executar la comanda git status que ens mostrarà quin és l’estat del repositori.

```sh
~/pardo-act01 git status
fatal: not a git repository (or any of the parent directories): .git
~/pardo-act01
```

Obtenim un error, que ens diu que no és un repositori. Això és normal, ja que per defecte, cap carpeta és un repositori. Perquè ho sigui, és a dir, per convertir-la en un repositoi, cal que executem la comanda git init.

```sh
~/pardo-act01$ git init
Initialised empty Git repository in /d/pardo-act01/.git/
~/pardo-act01$ 
```

Ens mostra el missatge (Initialised empty Git repository in /d/pardo-act01/.git/), és a dir, que s’ha inicialitzat com a repositori buit la ruta (/d/pardo-act01/.git/).
Tanmateix, si mirem el contingut de la carpeta pardo-act01 amb un ls -l o amb un dir, veiem que, aparentment no hi ha res creat.

```sh
~/pardo-act01$ ls -l
total 0
~/pardo-act01$
```

Però si executem la comanda perquè mostri els fitxers ocults ls -la o  dir /a, llavors sí que veiem que hi ha una carpeta nova anomenada .git, el que passa és que és oculta.

```sh
~/pardo-act01$ ls -a
total 12
drwxrwxr-x 3 profe profe 4096 Sep 24 13:00 .
drwxrwxrwx 7 profe profe 4096 Sep 24 13:00 ..
drwxrwxr-x 7 profe profe 4096 Sep 24 13:00 .git
~/pardo-act01$ 
```

Aquesta carpeta .git és la que conté tota la informació de git sobre el projecte. Cada vegada que es fan canvis, sigui afegint fitxers, sigui modificant el contingut dels fitxers, aquests canvis s’aniran guardant en aquesta carpeta. Per tant, és important que no l’esborreu, ni li feu res, ja que és imprescindible per poder interactuar amb git.

Si accedim a aquesta carpeta .git amb un cd .git, i llistem el contingut amb  ls -l o amb  dir podrem veure tot el contingut que necessita git per funcionar.

```sh
~/pardo-act01$ cd .git
~/pardo-act01/.git$ ls -l
total 32
drwxrwxr-x 2 profe profe 4096 Sep 24 13:00 branches
-rw-rw-r-– 1 profe profe   92 Sep 24 13:00 config
-rw-rw-r-– 1 profe profe   73 Sep 24 13:00 description
-rw-rw-r-– 1 profe profe   23 Sep 24 13:00 HEAD
drwxrwxr-x 2 profe profe 4096 Sep 24 13:00 hooks
drwxrwxr-x 2 profe profe 4096 Sep 24 13:00 info
drwxrwxr-x 4 profe profe 4096 Sep 24 13:00 objects
drwxrwxr-x 4 profe profe 4096 Sep 24 13:00 refs
~/pardo-act01/.git$ 
```

Però, si ara tornem enrere, amb cd .., és a dir, a la carpeta pardo-act01 i executem la comanda git -status, la resposta rebuda és una altra.

```sh
~/pardo-act01/.git$ cd ..
~/pardo-act01$ git status
On branch main

Initial commit

nothing to commit (create/copy files and use “git add” to track)

~/pardo-act01$
```

Ens mostra els següents missatges que volen dir:

On branch main, que ens trobem a la branca (branch) principal (main).
Initial commit nothing to commit, que des de l’inici de la confirmació (commit) no hi ha res per confirmar i per últim,
create/copy files and use "git add" to track, que si volem crear o copiar fitxers perquè comenci a gestionar la traçabilitat d’aquests, cal que fem servir la comanda git add <pathspec> (on <pathspec> és la llis ta dels fitxers que volem afegir al repositori).
Per tant, fins ara no hem fet res més que indicar quina és la carpeta del nostre repositori. Però ja estem preparats per crear i/o modificar fitxers i dur el control dels canvis que fem sobre aquests.

Afegir fitxers, i comandes status i commit.
Per començar crearem tres fitxers.

El primer l’anomenem index.html (codepen.io), i afegim el text bàsic per crear una pàgina web.

```html
<!DOCTYPE html>
<html lang="ca">
  <head>
    <meta charset="utf-8">
    <title>Activitat 1</title>
  </head>
  <body>
  
  </body>
</html>
```
Un cop que hem creat, modificat i guardat aquest primer fitxer, anem a veure què és el que ens diu git.


```sh
~/pardo-act01$ vi index.html

~/pardo-act01$ git status
On branch main

No commits yet

Untracked files:
  (use “git add <file>…” to include in what will be committed)
        index.html

nothing added to commit but untracked files present (use “git add” to track)
~/pardo-act01$ 
```

Ara apareix un nou missatge Untracked files, és a dir, fitxers sense traçar o controlar.

use "git add …" to include in what will be committed
utilitzeu “git add …” per incloure els fitxers a controlar.
nothing added to commit but untracked files present (use "git add" to track)
No hi ha res afegit per confirmar, però hi ha fitxers que no estan sent controlats. (Utilitzeu “git add …” per controlar).
I com a un d’aquests fitxers sense traça, que apareixen de color vermell, hi ha el index.html que acabem d’afegir, però com que no l’hem afegit al repertori, git encara no el reconeix i no el controla. Per molt que nosaltres el modifiquem, git mai el detectarà, ni controlarà els canvis.
Perquè git el tingui present, cal afegir-lo, i per això existeix la comanda git add <pathspec>.

```sh
~/pardo-act01$ git add index.html
~/pardo-act01$ git status
On branch main

No commits yet

Changes to be committed:
  (use “git rm ––cached …” to unstage)
        new file:   index.html

~/pardo-act01$ 
```

Un cop afegit el fitxer index.html, si tornem a executar la comanda git status, ara apareix un nou missatge “Changes to be committed” és a dir, canvis per ser controlats. I el fitxer index.html ara apareix com a nou i de color verd.

Ara és el moment de fer un commit. Un commit o confirmació és un punt intermedi en el nostre projecte. Acabarem tenint molts commit‘s, cada vegada que fem alguna cosa important o prou rellevant. Com un petit punt de control al qual sempre podrem tornar. Per tant, és recomanable realitzar aquests commit‘s, per exemple cada vegada es crea un nou fitxer, o afegim una única funció de javascript, o hem modificat alguns estils, etc. És a dir, cal fer un commit cada vegada que vulgui crear un punt de control, que vull recordar, o al que vull poder tornar més endavant.
Per fer-ho, cal fer servir, la comanda git commit amb el paràmetre -m, per afegir-li un missatge, comentari o nom que l’identifiqui. I tot i que és possible no afegir cap missatge, és molt recomenable, afegir-ne un que sigui útil i descriptiu sobre el que acabem de fer. Com per exemple, “afegir el fitxer index.html“.
Això ens serà molt útil per més endavant, per quan veiem el log dels commit‘s, puguem reconèixer a cadascun d’ells i saber que és el que vam fer just en aquell moment.

```sh
~/pardo-act01$ git commit -m “afegir el fitxer index.html”
[main (root-commit) 74859bc] afegir el fitxer index.html
1 file changed, 10 insertions(+)
create mode 100644 index.html

~/pardo-act01$ 
```

Ara afegirem dos fitxers més: main.js i styles.css

````sh
~/pardo-act01$ touch main.js
~/pardo-act01$ touch styles.css
~/pardo-act01$ ls -l
-rw-rw-r-– 1 profe profe 130 Sep 24 13:00 index.html
-rw-rw-r-– 1 profe profe   0 Sep 24 13:00 main.js
-rw-rw-r-– 1 profe profe   0 Sep 24 13:00 styles.css

~/pardo-act01$ 
```

I de moment els deixem buits i anem a veure què ha passat al git.

```sh
~/pardo-act01$ git status
On branch main
Untracked files:
  (use “git add <file>…” to include in what will be committed)
           main.js
           styles.css

nothing added to commit but untracked files present (use “git add” to track)

~/pardo-act01$
```# pardo-act01
