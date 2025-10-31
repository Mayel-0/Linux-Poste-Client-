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

# Avancé

## Exercice 1

Pour cette exercice au debut on doit seulment crée un utilisateur avec un répértoire personnel et un groupe

        sudo useradd -m Etudiant
        sudo groupadd Projet

on ajoute notre "Etudiant" dans notre groupe "Projet"

        sudo usermod -aG Projet Etudiant

<img src="/linux/Avance/exercice1/exercice1.1.png" height="100%" width="100%">

# TP 1

## 1 Installation et configuration d’un serveur web

On commence par installer **Apache2**, le serveur web le plus utilisé sur Linux.
Pour cela, on exécute la commande suivante :

    sudo apt update
    sudo apt install apache2 -y

Une fois installé, on vérifie qu’il fonctionne correctement :

        sudo systemctl enable apache2
        sudo systemctl start apache2
        sudo systemctl status apache2

Ensuite, on crée notre page web.
On remplace le contenu du fichier /var/www/html/index.html par le code qui est présent dans le tp :

On peut maintenant vérifier le fonctionnement du serveur en ouvrant un navigateur et en tapant :

        http://localhost ou http://<IP_DE_LA_VM>.

## 2 Modification du port du serveur

Par défaut, Apache écoute sur le port 80.
Nous allons le modifier pour qu’il écoute sur le port 8080.

On édite le fichier /etc/apache2/ports.conf :

sudo nano /etc/apache2/ports.conf

On remplace la ligne Listen 80 par Listen 8080.

Ensuite, on édite le fichier /etc/apache2/sites-available/000-default.conf et on modifie :

        <VirtualHost *:80>

par :

        <VirtualHost *:8080>

On redémarre Apache :

        sudo systemctl restart apache2

Le serveur est maintenant accessible sur :
http://localhost:8080.

## 3 Configuration du pare-feu avec UFW

On installe et configure UFW (Uncomplicated Firewall) pour sécuriser la machine.
L’objectif est d’autoriser uniquement les ports 22 (SSH) et 8080 (web).

Installation et configuration de base :

        sudo apt install ufw -y
        sudo ufw default deny incoming
        sudo ufw default allow outgoing

Autorisation des ports nécessaires :

        sudo ufw allow 22/tcp
        sudo ufw allow 8080/tcp

Activation du pare-feu :

        sudo ufw enable
        sudo ufw status

Désormais, seules les connexions SSH et HTTP (sur le port 8080) sont autorisées.

## 4 Sécurisation des connexions SSH

Pour améliorer la sécurité, on empêche la connexion via mot de passe et l’accès root.
On configure le service SSH pour n’accepter que les connexions par clé SSH.

On édite le fichier /etc/ssh/sshd_config :

        PasswordAuthentication no
        PubkeyAuthentication yes
        PermitRootLogin no

Puis on redémarre le service SSH :

sudo systemctl restart ssh

Le serveur SSH est maintenant sécurisé.

# TP 2

## 1 Préparation et configuration du webhook

Avant de commencer la surveillance, on crée un **webhook Discord** sur un serveur dédié aux alertes de sécurité.

### Étapes :
1. on ouvre le serveur Discord.
2. Va dans **Paramètres du salon → Intégrations → Webhooks → Nouveau webhook**.
3. Copie l’**URL du webhook** (elle sera utilisée dans les scripts d’alerte).

---

## 2 Surveillance des accès à des fichiers sensibles

### Objectif :
Détecter tout accès à un fichier sensible, par exemple :
`/etc/secret.txt`

### Installation de l’outil de surveillance :

        sudo apt install inotify-tools -y

### Script de surveillance :

On crée un fichier `/usr/local/bin/watch_secret.sh` :

celui ci contiendra donc le code que l'on nous a donner dans le TP

### Explications :

`inotifywait -e open` surveille les ouvertures du fichier.

Lorsqu’un accès est détecté, une alerte Discord est envoyée via curl.

On rend le script exécutable :

        sudo chmod +x /usr/local/bin/watch_secret.sh


Et on le lance en arrière-plan :

        nohup /usr/local/bin/watch_secret.sh &

## Surveillance des connexions SSH hors des horaires de bureau
Objectif :

Détecter toute connexion SSH en dehors des heures de bureau (9h00 à 18h00).

Script de surveillance :

On crée le fichier /usr/local/bin/check_ssh.sh :

#!/bin/bash
WEBHOOK_URL="https://discord.com/api/webhooks/YOUR_WEBHOOK_URL"

# Heure actuelle (format 24h)
CURRENT_HOUR=$(date +%H)

# On définit les horaires de bureau
START_HOUR=9
END_HOUR=18

# Si l'heure n'est pas dans la plage, on vérifie les connexions SSH récentes
if [ "$CURRENT_HOUR" -lt "$START_HOUR" ] || [ "$CURRENT_HOUR" -ge "$END_HOUR" ]; then
  # Recherche des connexions SSH récentes (dernières 5 minutes)
  if journalctl -u ssh -S -5m | grep "Accepted password" >/dev/null; then
    curl -H "Content-Type: application/json" \
         -X POST \
         -d "{\"content\": \"⚠️ Connexion SSH détectée en dehors des horaires de bureau !\"}" \
         $WEBHOOK_URL
  fi
fi


On rend le script exécutable :

        sudo chmod +x /usr/local/bin/check_ssh.sh

## 4 Automatisation avec cron pour une surveillance continue
Objectif :

Automatiser la surveillance en continu à l’aide de cron.

Configuration :

On édite la table cron :

        sudo crontab -e


Et on ajoute ces lignes :

# Lancer la surveillance du fichier secret au démarrage
@reboot nohup /usr/local/bin/watch_secret.sh &

# Vérifier les connexions SSH toutes les 5 minutes
*/5 * * * * /usr/local/bin/check_ssh.sh

Vérification :

Pour voir si les tâches sont bien actives :

        sudo crontab -l
