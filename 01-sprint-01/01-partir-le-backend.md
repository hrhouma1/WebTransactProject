# Installation et déploiement avec Docker Compose  

# Étape 1 : Télécharger le fichier `docker-compose.yml`  
Assurez-vous d'avoir le fichier `docker-compose.yml` dans un dossier de votre choix.

# Étape 2 : Installer Docker et Docker Compose  
Si Docker n'est pas encore installé, suivez ces étapes en fonction de votre système.  

### Windows / Mac  
- Télécharger et installer **Docker Desktop** depuis le site officiel : [https://www.docker.com/products/docker-desktop](https://www.docker.com/products/docker-desktop).  

### Linux (Ubuntu/Debian)  
Exécuter les commandes suivantes dans un terminal :  
```bash
sudo apt update
git clone https://github.com/hrhouma/install-docker.git
cd install-docker/
chmod +x install-docker.sh
./install-docker.sh
#ou sh install-docker.sh
docker version
docker compose version
apt-install docker-compose
docker-compose version
```

# Étape 3 : Télécharger et lancer les conteneurs  
Dans le dossier où se trouve le fichier `docker-compose.yml`, exécuter la commande suivante :  
```bash
docker-compose up -d
```
Cette commande télécharge automatiquement les images nécessaires et démarre les services.

# Étape 4 : Vérifier l'état des conteneurs  
Vérifier que les services sont bien en cours d’exécution avec la commande suivante :  
```bash
docker ps
```
Vous devriez voir trois conteneurs actifs :  
- `springboot_container` (Backend)  
- `mysql_container` (Base de données)  
- `phpmyadmin_container` (Interface MySQL)  

Le déploiement est terminé et les services sont opérationnels.



# Étape 5 : Accéder aux services déployés  

### Accès à l'API Spring Boot  
- Si l'application backend est configurée pour écouter sur le port 8080, elle devrait être accessible à l'adresse suivante :  
  ```
  http://localhost:8080
  ```
- Vérifier les logs du conteneur Spring Boot pour s'assurer qu'il fonctionne correctement :  
  ```bash
  docker logs springboot_container
  ```

### Accès à MySQL  
- Le service MySQL est accessible via le conteneur `mysql_container`.  
- Si un client MySQL est installé sur votre machine, vous pouvez vous y connecter avec la commande suivante :  
  ```bash
  mysql -h 127.0.0.1 -P 3306 -u root -p
  ```
- Par défaut, le mot de passe est défini dans le fichier `docker-compose.yml`.

### Accès à phpMyAdmin  
- phpMyAdmin permet de gérer la base de données via une interface web.  
- Il est accessible à l’adresse suivante :  
  ```
  http://localhost:8081
  ```
- Se connecter avec les identifiants configurés dans `docker-compose.yml` (généralement `root` comme utilisateur).

# Étape 6 : Gestion des conteneurs  

### Arrêter les conteneurs  
Pour arrêter tous les services en cours d'exécution, utiliser la commande :  
```bash
docker-compose down
```

### Relancer les conteneurs  
Si vous souhaitez relancer les services après les avoir arrêtés :  
```bash
docker-compose up -d
```

### Supprimer les conteneurs et les volumes  
Si vous souhaitez supprimer complètement les conteneurs ainsi que les volumes associés (les données MySQL seront perdues), utilisez :  
```bash
docker-compose down -v
```

# Étape 7 : Dépannage  

### Vérifier les logs d’un conteneur  
Si un conteneur ne fonctionne pas correctement, consulter ses logs pour identifier l'erreur :  
```bash
docker logs <nom_du_conteneur>
```
Exemple pour voir les logs du conteneur Spring Boot :  
```bash
docker logs springboot_container
```

### Vérifier l’état des conteneurs  
Si un service ne démarre pas correctement, vérifier son état :  
```bash
docker ps -a
```
Cela affiche tous les conteneurs, y compris ceux qui sont arrêtés.

### Redémarrer un conteneur spécifique  
Si un conteneur ne fonctionne pas comme prévu, le redémarrer avec :  
```bash
docker restart <nom_du_conteneur>
```

# Étape 8 : Mise à jour des services  
Si vous souhaitez mettre à jour une image Docker et relancer le service :  
```bash
docker-compose pull
docker-compose up -d
```

## Conclusion  
Le déploiement avec Docker Compose permet d'installer et de gérer rapidement des services tels que Spring Boot, MySQL et phpMyAdmin. En suivant ces étapes, vous pouvez facilement lancer, surveiller et maintenir votre application dans un environnement conteneurisé.
