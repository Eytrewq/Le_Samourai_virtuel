# Level12

Nous trouvons un script perl dans le home,
c'est un CGI servi sur le port 4646
Il prend deux paramètres en query, x et y
Le premier paramètre peut nous servir à faire une injection étant donné qu'il est utilisé dans une fonction non sécurisée , ou plutot dans la syntaxe perl des backticks.
Malheureusement le script tente de se protéger en remplacant les minuscules en majuscules et en supprimant tout caractère suivant un espace vide.

Donc pour contourner tout cela, nous créons un fichier en majuscule /tmp/GETFLAG dont nous ferons référence avec le wildcard (*) pour ne pas avoir à spécifier le dossier /tmp explicitement.

Nous spécifions en paramètre x ceci:

```bash
level12@SnowCrash:~$ curl localhost:4646?x=\`/*/GETFLAG\`
..
```
Nous obtenons le flag:

```bash
level12@SnowCrash:~$ cat /tmp/theflag
Check flag.Here is your token : XXXXXXXXXXXXXXXXXXXXXXXXX
```