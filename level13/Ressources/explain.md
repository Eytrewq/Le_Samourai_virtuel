# Level13

Le binaire s'attend à ce que l'uid de l'utilisateur éxécutant le programme soit 4242

```bash
level13@SnowCrash:~$ ./level13 
UID 2013 started us but we we expect 4242
```

Nous ne pouvons pas créer de nouvel utilisateur sans les droits roots. Nous devons trouver un autre moyen de faire croire au programme que notre UID vaut 4242.

Impossible de modifier la variable d'environnement UID:

```bash
level13@SnowCrash:~$ export UID="4242"
bash: UID: readonly variable
```

Un autre moyen consisterais à linker dynamiquement une librairie externe au programme, pour falsifier le retour de la fonction `getuid` utilisé dans le binaire.

Nous pouvons procéder comme ceci avec un compilateur comme gcc:

```c
int getuid() {
    return 4242;
}
```

```bash
level13@SnowCrash:/tmp$ gcc /tmp/getuid.c -fPIC -shared -o /tmp/getuid.so
```

Nous devons copier le binaire dans /tmp, pour que cette copie nous appartienne, afin de contourner la sécurité lié à la variable LD_PRELOAD. (Linux supprime cette variable si l'UID effectif n'est pas égal au UID réel)

UID réel = propriétaire du fichier

UID effectif = utilisateur du programme

```bash
level13@SnowCrash:/tmp$ cp ~/level13 .
```

```bash
level13@SnowCrash:/tmp$ LD_PRELOAD=/tmp/getuid.so ./level13
your token is XXXXXXXXXXXXXXXXXXXXXXXXX
```