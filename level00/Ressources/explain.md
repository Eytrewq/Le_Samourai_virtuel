# Level00

Quelques commandes de reconnaissance:

```bash
level00@SnowCrash:~$ pwd
/home/user/level00
```

```bash
level00@SnowCrash:~$ ls -la
total 12
dr-xr-x---+ 1 level00 level00  100 Mar  5  2016 .
d--x--x--x  1 root    users    340 Aug 30  2015 ..
-r-xr-x---+ 1 level00 level00  220 Apr  3  2012 .bash_logout
-r-xr-x---+ 1 level00 level00 3518 Aug 30  2015 .bashrc
-r-xr-x---+ 1 level00 level00  675 Apr  3  2012 .profile
```

```bash
level00@SnowCrash:~$ find / -user flag00 2>/dev/null
/usr/sbin/john
/rofs/usr/sbin/john
```

Nous avons trouvé un fichier /usr/sbin/john

```bash
level00@SnowCrash:~$ cat /usr/sbin/john
cdiiddwpgswtgt
```

On s'est douté que c'était crypté,
nous sommes allés sur dcode.fr, 
dans 'indentification chiffrement'

https://www.dcode.fr/identification-chiffrement

Il s'agit d'un code de césar, qu'on peut décodé en
"nottoohardhere"

```
level00@SnowCrash:~$ su flag00
Password: 
Don't forget to launch getflag !
flag00@SnowCrash:~$ getflag
Check flag.Here is your token : XXXXXXXXXXXXXXXXXXXXXXXXX
```