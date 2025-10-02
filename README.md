# Linux Exercice

## Exercice 1

Donc pour ce 1er exercie on nous demande simplement de crée un Dossier avec a l'interieur 2 Fichier et un autre Fichier cacher.

pour cela j'utiliser pour me deplacer les commandes

    /ls
    /ls -a
    /cd <nom du dossier>
    /cd ../

ensuite pour crée mes fichiers et dossiers j'ai utiliser

    /touch <nom du fichier.txt>
    /mkdire <nom du dossier>

Pour cacher mon ficher j'ai fait la commande si dessous

    /v fichier3.txt .fichier3.txt

et pour finir j'ai utiliser la commande.

    /cp Files/fichier1.txt copiefichier1.txt

<img src="/linux/exercice1/exercice1.png" height="100%" width="100%"/>

## Exercice 2

Pour cette exercice en premier lieux on nous demande de , Créer un fichier log.txt qui contient la liste des fichiers de /etc . donc on fait cela

pour cela j'utiliser pour me deplacer les commandes

    /ls
    /cd <nom du dossier>
    /cd ../

puis je crée mon fichier log.txt

    /touch log.txt

puis j'envoie le resultat de (ls /etc dans le log.txt)

    /ls /etc > log.txt

en utilisant (> ou >>) on indique donc que l'on ajout le resultat de notre commande au debut dans le fichier que l'on selectionne

<img src="/linux/exercice2/exercice2.1.png" height="100%" width="100%">

Vérification :

<img src="/linux/exercice2/exercice2.2.png" height="100%" width="100%">
<img src="/linux/exercice2/exercice2.3.png" height="60%" width="60%">

ensuite on nous demande d'Ajoute dans ce fichier les 10 dernières lignes du fichier /var/log/syslog
donc on fait cela

je regarde les 10 derniers lignes de mon fichier /var/log/syslog

    /tail -n 10 /var/log/syslog

et ensuite on fait pareille que avant en utilisant (>>)

<img src="/linux/exercice2/exercice2.4.png" height="100%" width="100%">

Vérification :

<img src="/linux/exercice2/exercice2.5.png" height="100%" width="100%">

et pour finir on nous demande, Affichez moi seulement les lignes qui contiennent le mot « error » donc on fait

    /grep 'error' <le dossier ou fichier viser>

<img src="/linux/exercice2/exercice2.6.png" height="100%" width="100%">
