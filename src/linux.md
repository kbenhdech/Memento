Linux
=====

Supprimer tout les processus contenant 'XXX' dans le nom :  `ps aux | grep XXX | awk  '{print \$2}' | xargs  kill -9`
