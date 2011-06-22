Linux
=====

Supprimer tout les processus contenant 'XXX' dans le nom :  `ps aux | grep XXX | awk  '{print \$2}' | xargs  kill -9`

Copier un fichier de/sur une autre machine : `scp root@192.168.0.0:/home/root/fromFile.txt home/kbenhdech/`
