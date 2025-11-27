# Minetest-server
Installation d'un serveur Minetest sur LXC avec un dashboard interactif
Présentation

Ce guide explique comment installer des serveurs Minetest sur des conteneurs LXC, ainsi que la mise en place d’un dashboard interactif pour gérer ces serveurs.

Installation de Minetest
Prérequis

Conteneurs LXC configurés (avec des adresses IP, etc.)

Système Debian/Ubuntu sur les conteneurs

Étapes d'installation

Installation des paquets nécessaires
Sur chaque conteneur, commencez par mettre à jour les dépôts et installer Minetest ainsi que les dépendances requises via APT :

apt update
apt install minetest-server iptables iptables-persistent fail2ban


Déplacement des fichiers de configuration
Transférez les fichiers nécessaires dans les répertoires correspondants :

minetest.conf de chaque monde dans /etc/minetest/

world.mt dans /var/games/minetest-server/.minetest/worlds/world/

sudoers dans /etc/

Le fichier de jail et le filtre minetest-auth.conf dans /etc/fail2ban/

Les fichiers index de Dashboard et Web dans /var/www/

Définir les permissions
Assurez-vous que les permissions sont correctement définies pour les répertoires et fichiers :

chown -R Debian-minetest:games /etc/minetest
chown -R Debian-minetest:games /usr/share/games/minetest
chown -R Debian-minetest:games /var/games/minetest-server


Redémarrer le service Minetest
Pour appliquer la configuration, redémarrez le serveur Minetest :

systemctl restart minetest-server

Configuration du DNAT

Pour rendre les cartes accessibles depuis l’extérieur, configurez les règles DNAT sur le serveur principal, en redirigeant les ports vers chaque conteneur. Exemple :

iptables -A PREROUTING -t nat -p udp --dport 30000 -j DNAT --to-destination 10.0.3.10:30000
iptables -A PREROUTING -t nat -p udp --dport 30001 -j DNAT --to-destination 10.0.3.15:30000


Note : Adaptez l'adresse IP et le port selon votre configuration.

Installation du Dashboard

Installation d'Apache et PHP

Sur le serveur principal, installez Apache et PHP pour faire tourner le dashboard :

apt update
apt install apache2 php php-cli php-common libapache2-mod-php


Configuration du Dashboard

Modifiez la configuration d’Apache dans /etc/apache2/sites-available/000-default.conf pour définir le répertoire racine du serveur Web où se trouve votre dashboard, comme suit :

DocumentRoot /var/www/minetest


Ensuite, définissez les bonnes permissions pour le répertoire :

chown -R www-data:www-data /var/www/minetest


Redémarrez Apache pour appliquer les modifications :

systemctl restart apache2


Si vous avez également un fichier index.html dans un sous-répertoire "Web", appliquez la même procédure de permission.

Personnalisation

Modifiez les fichiers index.php et index.html du dashboard selon vos besoins pour personnaliser l'interface utilisateur.

Installation des Scripts

Déplacement des scripts
Déplacez les scripts .sh dans le répertoire /usr/bin/.

Déplacement des fichiers de service systemd
Déplacez les fichiers .service dans /etc/systemd/system/.

Recharger systemd
Rechargez les fichiers de configuration de systemd :

systemctl daemon-reload


Appliquer les droits d’exécution
Assurez-vous que l'utilisateur www-data (l’utilisateur sous lequel Apache fonctionne) a les droits d'exécution sur les scripts :

chmod +x /usr/bin/vos_scripts.sh

Informations importantes

Ce dashboard est compatible avec les distributions utilisant :

LXC (Linux Containers)

Apache2

PHP

Contributions

Les contributions sont les bienvenues ! Vous pouvez :

Modifier et améliorer le code

Proposer des mises à jour

Signaler un problème via une issue

Soumettre une pull request pour vos améliorations
