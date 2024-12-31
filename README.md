Déploiement CI/CD avec Ansible - Bulletin Board
Description du projet

Ce projet vise à déployer une application de type Bulletin Board (tableau d'affichage) à l'aide d'Ansible. L'application est un exemple disponible sur GitHub et est utilisée pour illustrer un workflow CI/CD simple.
Projet choisi

    Nom du projet : Bulletin Board
    Lien vers le projet : Bulletin Board sur GitHub

Structure du dépôt

    Playbooks Ansible : Scripts pour déployer l'infrastructure et l'application.
    Docker-Compose : Fichier pour lancer le projet dans un environnement de conteneurisation.
    Documentation : Instructions pour exécuter les playbooks et accéder au projet.

Organisation des fichiers

Bulletin-Board/
├── playbooks/
│   ├── main.yml            # Playbook principal
│   ├── inventory.ini       # Fichier d'inventaire Ansible
├── roles/
│   ├── webserver/          # Rôle pour configurer le serveur web
│   ├── database/           # Rôle pour configurer MongoDB
│   ├── app/                # Rôle pour déployer l'application Node.js
├── docker-compose.yml      # Fichier Docker Compose
├── README.md               # Documentation du projet

Prérequis

    Docker Desktop (pour tester sur Windows ou Linux).
    Git (pour cloner ce dépôt).
    Une machine cible sous Ubuntu/Debian pour le déploiement (réel ou simulée dans Docker).

Instructions de déploiement
1. Cloner le dépôt

Ouvrez un terminal et exécutez la commande suivante :

git clone <URL_DU_DEPOT_GIT>
cd Bulletin-Board

2. Lancer le déploiement avec Ansible

    Vérifiez que vous êtes dans le dossier playbooks.
    Exécutez le playbook principal :

    ansible-playbook -i inventory.ini main.yml

Accéder au projet

Une fois le déploiement terminé :

    Serveur web : Accédez à l'application via http://localhost.
    Base de données : MongoDB est configuré en local sur la machine cible.

Membres du groupe

    Nom/Pseudo : [Ajoutez ici vos noms ou pseudos]
