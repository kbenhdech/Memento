Git
===

Fusionner deux commit :

* `git reset --soft HEAD~1` 
* `git commit -a --amend`

Editer le fichier de configuration : `git config --global --edit`

Affichage sexy des logs en ligne de commandes : `git log --graph --oneline --decorate`

Supprimer les modifications qui ont été ajoutée à l’index pour revenir à l'état du dernier commit : `git reset --hard HEAD`

Revenir à un commit antèrieur dont le sha1 est spécifié : `git reset --hard sha1`

Forcer un push : `git push -f`

Enlever de l'index un fichier : `git checkout -- file`

Créer une branche locale : `git checkout -b maBranche`

Créer une branche locale, connectée à une branche distante du même nom (qui existe) : `git checkout maBranch`

Lister l'ensemble des branches locale et distante : `git branch -a`

Supprimer une branche : `git branch -D maBranch` 

Création d'une branche locale, connectée à une branche distante : `git checkout --track -b brancheLocal brancheDistante`

Mettre à jour l'index et la liste des branches/tags : `git fetch origin --all`

Créer une branche locale qui est connecté à une branche distante : `git checkout -b --track maBranche origin/maBranche`

Afficher les logs : `git log`

Revenir à un état antérieur qui n'est pas à proprement parlé un commit (~nous sauver de la mort !) : `git reflog`

Envoyer les modifications de la branche locale sur la branche distante : `git push origin origin:refs/heads/maBranche`

Ajouter un repository distant : `git remote add repoDistant ssh://login@domaine.tld/~login/monRepo`

Executer une commande git sur un repositoy git qui n'est pas dans le répertoire courant : `git --git-dir=/monRepo/.git --work-tree=/monRepo commande`




