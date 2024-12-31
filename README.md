# **Déploiement CI/CD avec Ansible - Bulletin Board**

## **Description du projet**
Ce projet vise à déployer une application de type **Bulletin Board** (tableau d'affichage) à l'aide d'Ansible. L'application est un exemple disponible sur GitHub et est utilisée pour illustrer un workflow CI/CD simple.

### **Projet choisi**
- **Nom du projet** : Bulletin Board
- **Lien vers le projet** : (https://github.com/rsinghcodes/Bulletin-Board)

---

## **Structure du dépôt**
- **Playbooks Ansible** : Scripts pour déployer l'infrastructure et l'application.
- **Docker-Compose** : Fichier pour lancer le projet dans un environnement de conteneurisation.
- **Documentation** : Instructions pour exécuter les playbooks et accéder au projet.

### **Organisation des fichiers**
```
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
```

---

## **Prérequis**
1. **Docker Desktop** (pour tester sur Windows ou Linux).
2. **Git** (pour cloner ce dépôt).
3. Une machine cible sous **Ubuntu/Debian** pour le déploiement (réel ou simulée dans Docker).

---

## **Instructions de déploiement**

### **1. Cloner le dépôt**
Ouvrez un terminal et exécutez la commande suivante :
```bash
git clone <[URL_DU_DEPOT_GIT]>
cd Bulletin-Board
```

### **2. Lancer le déploiement avec Ansible**
1. Vérifiez que vous êtes dans le dossier `playbooks`.
2. Exécutez le playbook principal :
   ```bash
   ansible-playbook -i inventory.ini main.yml
   ```

---

## **Accéder au projet**
Une fois le déploiement terminé :
- **Serveur web** : Accédez à l'application via [http://localhost](http://localhost).
- **Base de données** : MongoDB est configuré en local sur la machine cible.

---

## **Membres du groupe**
- **Nom/Pseudo** : Thibaud (meilleur membre du groupe)

---

## **Fichier Docker-Compose**
Le fichier `docker-compose.yml` permet de lancer les services nécessaires à l'application. Voici son contenu :

```yaml
version: '3.8'

services:
  app:
    image: node:14
    container_name: bulletinboard_app
    working_dir: /app
    volumes:
      - ./Bulletin-Board:/app
    ports:
      - "3000:3000"
    command: bash -c "npm install && npm start"

  mongodb:
    image: mongo:latest
    container_name: bulletinboard_db
    ports:
      - "27017:27017"

  nginx:
    image: nginx:latest
    container_name: bulletinboard_web
    ports:
      - "80:80"
    volumes:
      - ./roles/webserver/files/nginx.conf:/etc/nginx/conf.d/default.conf
```

Pour lancer le projet via Docker Compose :
```bash
docker-compose up -d
```

---
