Linux
=====



Commandes
---------

Supprimer tout les processus contenant 'XXX' dans le nom :  `ps aux | grep XXX | awk  '{print \$2}' | xargs  kill -9`

Copier un fichier de/sur une autre machine : `scp root@192.168.0.0:/home/root/fromFile.txt home/kbenhdech/`

Télécharger un fichier : `wget http://www.site.com/file.txt`

Créer un lien symbolique : `ln -s file symlink`
+
Dézipper un fichier avec l'extension .tar.gz : `tar xvzf file.tar.gz`

Dézipper un fichier avec l'extension .tar : `tar xf file.tar`

Dézipper un fichier avec l'extension .gz : `gzip -d file.gz`

Rechercher dans les fichiers du répertoire courant (récursivement) : 

* `ack-grep word`
* `find ./ -print0 | xargs --null grep word`

Sed : http://www.system-linux.eu/index.php?post/2008/12/21/La-commande-Sed

Aperçu amélioré des fichiers du répertoire courant : `ls -lah`

Espace disque total occupé par le répertoire courant: `du -chs`

Recherche rapide de commande : `ctrl+r` dans console

Informations sur les points de montage : `df -h`

Lancer une commande sur un serveur distant : `ssh -f root@production-web.vidal.net "cd /data/produits/production/production-auto-web; play run"`

Voir les dernières lignes d'un fichier : `tail -f file`

Redemarrer : `reboot`

Récupérer les informations hardware de sa machine : `lshw`

Afficher des informations sur les connexions réseau : `netstat -anpe`

Lister les fichiers actuellement ouverts sur le système : `lsof`

Détecter si le système UNIX n'est pas compromis par un rootkit. : `chkrootkit`

Détecter si le système UNIX n'est pas compromis par des rootkits, portes dérobées et exploits. : `rkhunter --check`

Synchroniser deux répertoires : `rsync -vart origine destination`

Avoir des informations sur le trafic réseau en temps réel : `ntop`

Rechercher un mot récursivement dans des fichiers : `ack-grep mot`

Faire une mise à jour : `sudo apt-get upgrade -f --fix-missing`

Remplacer une chaine de caractère (ici "vidal") par une autre chaine de caractère (ici "ubm") dans des fichiers (portant ici l'extension .xml), récursivement : `find . -name "*.xml" -type f -exec sed -i "s/vidal/ubm/g" {} \;`


Fichiers
--------

* .bashrc

Connaître la taille d'un répertoire : `du -sh repertoire`





Liens intéressants
------------------

[Aide-mémoire](http://www.dti.ulaval.ca/pp/rva/unix/Unix_AideMemoire.htm)






Postfix
-------

Fichier de configuration : `/etc/postfix/main.cf`





Ajouter un utilisateur à courier-imap
-------------------------------------

Utilisateur : asmaa
Mot de passe majidi

        adduser asmaa
        cd /home/asmaa/
        sudo maildirmake Maildir
        chmod 777 -R Maildir/
        chown asmaa:asmaa -R Maildir/
        usermod -s /bin/false asmaa
        echo "majidi" | userdbpw | userdb "asmaa" set imappw
        userdb "asmaa" set mail=/home/asmaa/Maildir
        makeuserdb
        /etc/init.d/courier-imap restart





Configuration DNS
-----------------

Domaine : karim-benhdech.fr
Sous domaine : blog.karim-benhdech.fr

Editez le fichier /etc/bind/named.conf.local :

        zone "karim-benhdech.fr" {
            type master;
            allow-transfer {
                213.186.33.199;
            };
            file "/etc/bind/karim-benhdech.fr.hosts";
            notify yes;
        };


Editez le fichier /etc/bind/karim-benhdech.fr.hosts :

        $TTL 3600
        karim-benhdech.fr.      IN      SOA     ks370096.kimsufi.com. karim-benhdech.gmx.fr. (
                        2011110701 ;serial
                        300 ;refresh
                        900 ;retry
                        604800 ;expire
                        3600 ;default_ttl
        )
        
        karim-benhdech.fr.              IN    NS        ks370096.kimsufi.com.
        karim-benhdech.fr.              IN    NS        ns.kimsufi.com.

        karim-benhdech.fr.              IN    MX        10 mail.karim-benhdech.fr.

                        IN    A         94.23.14.61
        blog            IN    A         94.23.14.61
        mail            IN    A         94.23.14.61
        dms             IN    A         94.23.14.61
        webmail         IN    A         94.23.14.61
        mail            IN    A         94.23.14.61
        www             IN    A         94.23.14.61

Editez le fichier /etc/bind/named.conf.options :


        options {
                directory "/var/cache/bind";
        
        
                forwarders {
                        //213.186.33.199;
                };

                auth-nxdomain no;    # conform to RFC1035
                listen-on-v6 { any; };
                listen-on { any; };

               // Les adresses autorise a interroger de facon recursive le serveur DNS
                allow-recursion {
                        127.0.0.1;
                        94.23.14.61;
                };

                // Autorise le transfert de zone uniquement pour ns.kimsufi.com pour notre cas
                allow-transfer {
                        213.186.33.199;
                };
        };


Redemarrez :

        /etc/init.d/bind9 restart
        sudo invoke-rc.d bind9 reload

Testez :

        nslookup blog.karim-benhdech.fr







Configuration apache
--------------------
       
Editez le fichier /etc/apache2/sites-available/default :

        <VirtualHost *>
        ServerName karim-benhdech.fr
        DocumentRoot /home/www/blog
        ServerAlias www.karim-benhdech.fr
        </VirtualHost>  
        
        
Editez le fichier /etc/apache2/sites-available/blog.karim-benhdech.fr :

        <VirtualHost *>
        ServerName blog.karim-benhdech.fr
        DocumentRoot /home/www/blog/
        </VirtualHost>  
   

Lancez la commande :   
  
        a2ensite blog.karim-benhdech.fr            

Redemarrez :

        /etc/init.d/apache2 restart                            




Utilisateurs
------------

userdel asmaa

adduser karim

usermod -s /bin/false karim

vi /etc/passwd



Screen
------

Voir la liste des fenêtres ouvertes : `ctrl-a +w`

Créer une fenêtre : `ctrl-a +c`

Aller à la fenêtre [numéro de fenetre] : `ctrl-a +[numéro de fenetre]`

Stopper screen : `ctrl-a +d`

Lancer screen avec la dernière session : `screen -r`


Autres
------

cowsay
fortune
yes





Shell
-----

TODO

etc/shells

kornshell
zsh complétion amélioré

