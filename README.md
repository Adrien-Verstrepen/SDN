# Documentation git 

## Installer un projet git et configurer pour pouvoir faire des changements

### Installation de git : 
Git sur Linux : ```sudo apt install git-all```

Git sur Windows : ```winget install --id Git.Git -e --source winget```

Git sur Windows : https://git-scm.com/download/win

### Installation du projet :

* Ouvrir un terminal dans « documents »
* Utiliser les commandes suivantes :
    1. HTTPS :
On créé un dossier github dans documents puis :
On ouvre le dossier (repository) sur lequel on souhaite travailler, on clique le bouton vert "code" et on copie l'URL https. 
Dans git bash on execute : ```git clone [l'URL]```

 2. SSH : 
On créé un dossier github dans documents puis :
On ouvre le repository sur lequel on souhaite travailler, on clique le bouton vert "code" et on va dans ssh. 
On execute ```git clone```la commande donnée dans le git bash et on récupère le dossier.

### Comment on utilise git ?
Une fois qu'on a cloné le repo, on va dans le dossier correspondant puis on créé la branche sur laquelle on va travailler : 
```git checkout -b [NOM_BRANCHE]```
Une fois qu'on est satisfait des changements : 
```git add .```
```git commit -m "message"```
```git push```

En cas d'erreur : "fatal: The current branch [NOM_BRANCHE] has no upstream branch." il faut executer ```git push --set-upstream origin [NOM_BRANCHE]```

Une fois que la feature / fix est correctement implémenté, on fait une pull request : ```git request-pull```

### Création clé SSH
On vérifie qu'on a une clé ssh ajoutée sur github sinon on en créée une : 
Dans git bash : ```ssh-keygen -t rsa 4096 -C "ton_mail@exemple.com"```
Cela génère la paire de clé privée / publique pour ssh.
Le nom du fichier peut rester id_rsa mais attention à ne pas écraser des clés existantes.
On peut entrer un mot de passe ou non.

On vient par la suite ajouter la clé ssh à l'agent ssh :
On ouvre un Power Shell en admin puis on execute : ```Get-Service -Name ssh-agent | Set-Service -StartupType Manual``` puis ```Start-Service ssh-agent```

Ensuite dans le git bash : ```ssh-add C:/Users/YOU/.ssh/id_rsa```

On peut maintenant aller copier la clé ssh dans le github. Dans un terminal : ```clip < /.ssh/id_rsa.pub```
Et on va sur : https://github.com/settings/ssh/new
On clique sur add SSH key et c'est bon !

## Le fonctionnement de git

![gitflow](https://github.com/AdrienVerstrepen/SDN/assets/145664365/9832e51e-4314-42d9-9eb9-a1702ceda1e0)

La branche master est la branche principale où l'on a la version de production de l'application / code

La branche develop nous servira à fusionner les branches de développement des fonctionnalités / fix

Les branches features sont indépendantes : une fonctionnalité = une branche
