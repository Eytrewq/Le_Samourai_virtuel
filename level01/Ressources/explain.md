# Level01

à force de recherches, nous avons trouvé une entrée intriguante dans /etc/passwd, commançant par '42' (comme de par hasard)

```bash
level01@SnowCrash:~$ cat /etc/passwd
...
flag01:42hDRfypTqqnw:3001:3001::/home/flag/flag01:/bin/bash
...
```

On copie le fichier sur la machine hote

```bash
scp -P 4242 level01@192.168.56.101:/etc/passwd .
```

Depuis la machine hôte, on utilise john pour cracker
le mot de passe crypté:

```bash
 ✘ user42@user42-X751LN  ~/Documents/snowcrash  john passwd -show
flag01:abcdefg:3001:3001::/home/flag/flag01:/bin/bash

1 password hash cracked, 0 left
```

Le mot de passe "abcdefg" nous permet de nous connecter au user flag01 et d'obtenir le flag

```bash
flag01@SnowCrash:~$ getflag
Check flag.Here is your token : XXXXXXXXXXXXXXXXXXXXXXXXX
```