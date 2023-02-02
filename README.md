# Explicació de git

[Git Tutorial](https://www.w3schools.com/git/default.asp?remote=github)

# Index

## [Instal·lar git a Windows](./README.md#installar-git-a-windows-1)
## [Comanda **```git status```** per veure l'estat del repositori](./README.md#comanda-git-status-per-veure-lestat-del-repositori-1)
## [Inicialitzar un repositori](./README.md#inicialitzar-un-repositori-1)

## [Afegir fitxers, i comanda **```commit```**.](./README.md#afegir-fitxers-i-comanda-commit-1)

## [Setting your commit email address](./README.md#setting-your-commit-email-address-1)

## [Setting your username in Git](./README.md#setting-your-commit-email-address-1)

## Creació d'un usuari a [github.com](./README.md#creacic3b3-dun-usuari-a-githubcom-1)

## Creació d'un repositori a la vostre compta a [github.com](./README.md#creació-dun-repositori-a-la-vostre-compta-a-githubcom-1)

## Com convidar a un col·laborador a un repositori a la vostre compta a [github.com](./README.md#com-convidar-a-un-collaborador-a-un-repositori-a-la-vostre-compta-a-githubcom-1)

## [Inviting collaborators to a personal repository](./README.md#inviting-collaborators-to-a-personal-repository)





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

# Comanda **```git status```** per veure l'estat del repositori


Existeix una comanda que ens mostra en quin estat es trova el nostre repositori.

Un cop ja siguem dins de la carpeta que acabem de crear podem provar d'executar la comanda **``git status``** que ens mostrarà quin és l'estat del repositori.

```sh
~/pardo-act01 git status
fatal: not a git repository (or any of the parent directories): .git
~/pardo-act01
```

Obtenim un error, que ens diu que no és un repositori. Això és normal, ja que per defecte, cap carpeta és un repositori.

# Inicialitzar un repositori

Per fer  que la nostra carpeta sigui un repositori, és a dir, per dir-li a `**```git```**` que volem que porti el control dels canvis al fitxers, cal que executem la comanda **```git init```**.

```sh
~/pardo-act01$ git init
Initialised empty Git repository in /d/pardo-act01/.git/
~/pardo-act01$ 
```

Ens mostra el missatge (**```Initialised empty Git repository in /d/pardo-act01/.git/```**), és a dir, que s'ha inicialitzat com a repositori buit la ruta (**``/d/pardo-act01/.git/``**).`

Tanmateix, si mirem el contingut de la carpeta **``pardo-act01``** amb un `**```ls -l```**` o amb un **```dir```**, veiem que, aparentment no hi ha res creat.

```sh
~/pardo-act01$ ls -l
total 0
~/pardo-act01$
```

Però si executem la comanda perquè mostri els fitxers ocults **``ls -la``** o  `**``dir /a``**`, llavors sí que veiem que hi ha una carpeta nova anomenada `**```.git```**`, el que passa és que és oculta.

```sh
~/pardo-act01$ ls -a
total 12
drwxrwxr-x 3 profe profe 4096 Sep 24 13:00 .
drwxrwxrwx 7 profe profe 4096 Sep 24 13:00 ..
drwxrwxr-x 7 profe profe 4096 Sep 24 13:00 .git
~/pardo-act01$ 
```

Aquesta carpeta **```.git```** és la que conté tota la informació de **```git```** sobre el projecte. Cada vegada que es facin canvis, ja sigui afegint fitxers, modificant el contingut dels fitxers, creant o esborrant subcarpetes ,etc aquests canvis s'aniran guardant en aquesta carpeta. Per tant, **és important** que no l'esborreu, ni li feu res, ja que és **imprescindible** per poder interactuar amb **```git```**.

Si accedim a aquesta carpeta **```.git```** amb un ```cd .git```, i llistem el contingut amb  ```ls -l``` o amb  ```dir``` podrem veure tot el contingut que necessita **```git```** per funcionar.

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

Però, si ara tornem enrere, amb **```cd ..```**, és a dir, a la carpeta **```pardo-act01```** i executem la comanda **```git -status```**, la resposta rebuda és una altra.

```sh
~/pardo-act01/.git$ cd ..
~/pardo-act01$ git status
On branch main

No commits yet

nothing to commit (create/copy files and use "git add" to track)

~/pardo-act01$
```

Ens mostra els següents missatges que volen dir:

* **```On branch main```**, que ens trobem a la branca (**```branch```**) principal (**```main```**)
* **```No commits yet```**, que encara no hi ha res per confirmar (**```commit```**) i per últim,
* **```(create/copy files and use "git add" to track)```**, que si volem afegir fitxers perquè comenci a gestionar la traçabilitat d'aquests, cal que fem servir la comanda **```git add```** per afegir els fitxers a la llista dels fitxers que volem afegir al repositori.

Per tant, fins ara no hem fet res més que indicar quina és la carpeta del nostre repositori. Però ja estem preparats per crear i/o modificar fitxers i dur el control dels canvis que fem sobre aquests.


# Afegir fitxers, i comanda **```commit```**.

Per començar crearem tres fitxers.

**```index.html```**, **```main.js```** i **```styles.css```**.

El primer l'anomenem **```index.html```** ([pardo-act01 (codepen.io)](https://codepen.io/joanpardo/pen/QWBzLwp)), i afegim el text bàsic per crear una pàgina web.

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
Un cop que hem creat, modificat i guardat aquest primer fitxer, anem a veure què és el que ens diu **```git```**.

```sh
~/pardo-act01$ vi index.html
```


```sh
~/pardo-act01$ git status
On branch main

No commits yet

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        index.html

nothing added to commit but untracked files present (use "git add" to track)
~/pardo-act01$ 
```

Ara apareix una secció **```Untracked files```**, és a dir, una apartat a on ens mostra aquells fitxers, que no estan **marcats** per controlar els seus els canvis, és a dir que **NO tenen de traça**. És a dir, que el fitxer **```index.html```**, no està marcat per controlar els canvis que es facin sobre ell.

A part, apareix la següent explicació:
```sh
use "git add ..." to include in what will be committed

```


La comanda **```git add ...```** afegeix un fitxer al repositori local i el prepara per a la confirmació. Per eliminar o treure un fitxer, cal fer servir **```git reset HEAD <<nomFitxer>>```**.

És a dir, que cal fer servir "**```git add ...```**" per incloure els fitxers que volem que **```git```** comenci a controlar.

I per útlim ens indica:

```sh
nothing added to commit but untracked files present (use "git add" to track)
```

Que tot i que hi ha **fitxers sense traça** (**```untracked files```**), no hi ha res afegit per **confirmar**, és a dir per incloure en el següent control. I ens indica que cal fer per afeir fitxers al control, "**```(use "git add" to track)```**, és a dir feu servir **```git add```** per afegir fitxers a traçar.

Fixeu-vos que aquests fitxers sense traça, apareixen de color vermell, i en el nostre cas apareix el fitxer **```index.html```** que acabem d'afegir, però com que no l'hem afegit al control de traça, **``git``** encara no el `té a la llista de fitxers a controlar. Ara mateix, per molt que nosaltres el modifiquem, **``git``** mai el detectarà, ni controlarà els canvis`que pateixi.

## Afegir fitxers

Perquè **```git```** tingui present el fitxer **```index.html```**, cal afegir-lo, i per això existeix la comanda **```git add <pathspec>```**.

```sh
~/pardo-act01$ git add index.html
```

```sh
~/pardo-act01$ git status
On branch main

No commits yet

Changes to be committed:
  (use "git rm ––cached ..." to unstage)
        new file:   index.html

~/pardo-act01$ 
```

Un cop afegit el fitxer **```index.html```**, si tornem a executar la comanda **```git status```**, ara apareix un nou missatge "**```Changes to be committed```**" és a dir, canvis per ser controlats. I el fitxer **```index.html```** ja apareix com a fitxer nou i de color verd.

Ara és el moment de fer un **```commit```**. Un **```commit```** o **confirmació** és un **punt de control** en el nostre projecte. Acabarem tenint molts **```commit```**'s, cada vegada que fem alguna cosa important o prou rellevant. Com un petit **punt de control** al qual sempre podrem tornar. Per tant, és recomanable realitzar aquests **```commit```**'s, per exemple cada vegada es crea un nou fitxer, o afegim una única funció de **```javascript```**, o hem modificat alguns estils, etc. És a dir, cal fer un **```commit```** cada vegada que es vulgui crear un **punt de control**, que volem recordar, o al que volem poder tornar més endavant.
Per fer-ho, cal fer servir, la comanda git **```commit```** amb el paràmetre **```-m```**, per afegir-li un **missatge**, comentari o nom que l'identifiqui. I tot i que és possible no afegir cap missatge, és molt recomenable, afegir-ne un que sigui útil i descriptiu sobre el que acabem de fer. Com per exemple, "**```Creat el fitxer index.html```**".
Això ens serà molt útil per més endavant, per quan veiem el log dels **```commit```**'s, puguem reconèixer a cadascun d'ells i saber que és el que vam fer just en aquell moment.

```sh
~/pardo-act01$ git commit -m "Creat el fitxer index.html"
[main (root-commit) 74859bc] Creat el fitxer index.html
1 file changed, 10 insertions(+)
create mode 100644 index.html

~/pardo-act01$ 
```

Ara afegirem dos fitxers més: **```main.js```** i **```styles.css```**

```sh
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
  (use "git add <file>..." to include in what will be committed)
           main.js
           styles.css

nothing added to commit but untracked files present (use "git add" to track)

~/pardo-act01$
```

Abans de seguir cal confirmar que tenim la nostra instal·lació de git al nostre ordinador ben configurat.


## [Setting your commit email address](https://docs.github.com/en/account-and-profile/setting-up-and-managing-your-personal-account-on-github/managing-email-preferences/setting-your-commit-email-address)

## [Setting your username in Git](https://docs.github.com/en/get-started/getting-started-with-git/setting-your-username-in-git)

# Creació d'un usuari a [github.com](https://github.com/)

[Signing up for a new GitHub account](https://docs.github.com/en/get-started/signing-up-for-github/signing-up-for-a-new-github-account)


# Creació d'un repositori a la vostre compta a [github.com](https://github.com/)

[Create a repo](https://docs.github.com/en/get-started/quickstart/create-a-repo)

# Com convidar a un col·laborador a un repositori a la vostre compta a [github.com](https://github.com/)

[Inviting collaborators to a personal repository](https://docs.github.com/en/account-and-profile/setting-up-and-managing-your-personal-account-on-github/managing-access-to-your-personal-repositories/inviting-collaborators-to-a-personal-repository)

