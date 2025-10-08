# Debutant

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

<img src="/linux/debutant/exercice1/exercice1.png" height="100%" width="100%"/>

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

<img src="/linux/debutant/exercice2/exercice2.1.png" height="100%" width="100%">

Vérification :

<img src="/linux/debutant/exercice2/exercice2.2.png" height="100%" width="100%">
<img src="/linux/debutant/exercice2/exercice2.3.png" height="60%" width="60%">

ensuite on nous demande d'Ajoute dans ce fichier les 10 dernières lignes du fichier /var/log/syslog
donc on fait cela

je regarde les 10 derniers lignes de mon fichier /var/log/syslog

    /tail -n 10 /var/log/syslog

et ensuite on fait pareille que avant en utilisant (>>)

<img src="/linux/debutant/exercice2/exercice2.4.png" height="100%" width="100%">

Vérification :

<img src="/linux/debutant/exercice2/exercice2.5.png" height="100%" width="100%">

et pour finir on nous demande, Affichez moi seulement les lignes qui contiennent le mot « error » donc on fait

    /grep 'error' <le dossier ou fichier viser>

<img src="/linux/debutant/exercice2/exercice2.6.png" height="100%" width="100%">

## Exercice 3

cette exerice est simple on peut le voir juste avec ce screen on doit crée un fichier secret.txt et il faut que le propriétaire soit le seul a pourvoir écrire et lire ce fichier donc pour ca on decompose en 3 (6, 0, 0) le premier chiffre et pour le propriétaire le second pour le groupe et le dernier pout les aure en fesant cela on repond a l'exercice.

    /chmod 600 secret.txt

et pour me deplacer encore on utliser

    /ls
    /ls -l (pour afficher les permission)
    /cd <nom du dossier>
    /cd ../

<img src="/linux/debutant/exercice3/exercice3.1.png" height="100%" width="100%">

# Intermédiaire

## exercice 1

Dans cette exercice on nous demande de Affichez la liste des processus.
donc moi j'utlise Htop au lieux de top.

    /htop

<img src="/linux/intermediaire/exercice1/exercice1.1.png" height="100%" width="100%" >

Voici ce qui utilise la plus ma ram on peut le lire grace au %mem on voit que mes Shell sont a 12.2 il sont en premier si on clique sur ShortBy et qu'on trie pour avoir juste la ram (Percent_mem)

<img src="/linux/intermediaire/exercice1/exercice1.2.png" height="100%" width="100%">

Enusite on peut utiliser F8 ou F7 donc Nice - ou Nice + pour choisir la priorité des taches pour notre procésseur
on peut voir les changement dans le Pri et le NI pour Nice

<img src="/linux/intermediaire/exercice1/exercice1.3.png" height="100%" width="100%">

Ensuite on selectionne la tache que lon veut Kill (F9) ensuite on a plus qu'a send et on peut fermer FireFoxe en utilisant Htop

<img src="/linux/intermediaire/exercice1/exercice1.4.png" height="100%" width="100%">

## exercice 2

        tar -czf "/home/mayel/backups/backup-$(date +%Y%m%d).tar.gz" /home/mayel/Documents

<img src="/linux/intermediaire/exercice2/exercice1.1.png" height="100%" width="100%">

ce que l'on doit faire c'est crée un fichier backup.sh qui contien notre ligne de commande donc la

        tar -czf "/home/mayel/backups/backup-$(date +%Y%m%d).tar.gz" /home/mayel/Documents

et on vas ajouter cela a notre

        crontab -e (édité)
        crontab -l (afficher)

on lui rajoute le droit d'étre exécuté

        chmod +x /home/mayel/backup.sh

pour edité crontab, de la on lui ajout la ligne qui exécute notre backup.sh qui continent notre ligne de commande qui donc sera exécuté 0 2 = a 2h de matin tou les jours

        0 2 * * * /home/mayel/backup.sh

<img src="/linux/intermediaire/exercice2/exercice1.2.png" height="100%" width="100%">

## Exercice 3

crée un fichier
        touch sshd_failed_logins.txt
on peut tout faire juste avec cette commande
        journalctl -u ssh -S "24 hours ago" | grep -i "failed" >> sshd_failed_logins.txt

La 1er partie c'est pour afficher les log
        journalctl -u ssh -S "24 hours ago"

La deuxieme partie c'est pour afficher les erreur "failed" et les envoyer vers sshd_failed_logins.txt
        grep -i "failed" >> sshd_failed_logins.txt

<img src="/linux/intermediaire/exercice3/exercice3.1.png" height="100%" width="100%">
