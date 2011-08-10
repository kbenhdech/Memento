Linux
=====

Commandes
---------

Supprimer tout les processus contenant 'XXX' dans le nom :  `ps aux | grep XXX | awk  '{print \$2}' | xargs  kill -9`

Copier un fichier de/sur une autre machine : `scp root@192.168.0.0:/home/root/fromFile.txt home/kbenhdech/`

Télécharger un fichier : `wget http://www.site.com/file.txt`

Créer un lien symbolique : `ln -s file symlink`

Dézipper un fichier avec l'extension .tar.gz : `tar xvzf file.tar.gz`

Dézipper un fichier avec l'extension .tar : `tar xf file.tar`

Dézipper un fichier avec l'extension .gz : `gzip -d file.gz`

Rechercher dans les fichiers du répertoire courant (récursivement) : 

* `ack-grep word`
* `find ./ -print0 | xargs --null grep word`

Sed : http://www.system-linux.eu/index.php?post/2008/12/21/La-commande-Sed



Fichiers
--------

* .bashrc

Connaître la taille d'un répertoire : `du -sh repertoire`



Liens intéressants
------------------

[Aide-mémoire](http://www.dti.ulaval.ca/pp/rva/unix/Unix_AideMemoire.htm)


