# Level09

Un fichier 'token' nous sort du binaire

```bash
level09@SnowCrash:~$ cat token
f4kmm6p|=�p�n��DB�Du{��
```

Un programme nous permet d'encoder une chaine de caractère passée en argument

```bash
level09@SnowCrash:~$ ./level09 aaaaaaaaaaaaaaaaaaaaaaaaaa
abcdefghijklmnopqrstuvwxyz
```

Nous comprenons rapidement que le programme est un encoder, et qu'il faut donc décoder le fichier token pour obtenir le mot de passe.

Nous écrivons un petit script en python sur la machine hôte pour décripter le fichier.

```python
import sys

for i, j in enumerate(sys.argv[1]):
    sys.stdout.write(chr(ord(j) - i))
```

Nous utilisons notre script sur le fichier token

```bash
user42@user42-X751LN  ~/Documents/snowcrash  
python script.py $(cat token)
f3iji1ju5yuevaus41q1afiuq
```

Ce qui nous donne le mot de passe du flag09:

```bash
flag09@SnowCrash:~$ getflag
Check flag.Here is your token : XXXXXXXXXXXXXXXXXXXXXXXXX
```