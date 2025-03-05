# Déploiement du backend avec Docker Compose  

## **Présentation**  
Ce projet permet de déployer le backend de l’application via Docker Compose. Il inclut les corrections du Super Admin (Sprint 1) et sera mis à jour avec de nouvelles fonctionnalités dans le Sprint 2.

## **Prérequis**  
Avant de commencer, assurez-vous d’avoir :  
- **Docker** installé sur votre machine  
- **Docker Compose** installé  
- Une connexion Internet active pour récupérer l’image Docker  

## **Installation et exécution**  

### **1. Télécharger le fichier `docker-compose.yml`**  
Assurez-vous d’avoir le fichier `docker-compose.yml` dans votre répertoire de travail.  

### **2. Télécharger l’image Docker du backend**  
Récupérez la dernière version du backend en exécutant la commande suivante :  
```bash
docker pull mohsenfennnira/newtechmindbackend:sprint1
```

### **3. Lancer les services avec Docker Compose**  
Démarrez les conteneurs en arrière-plan avec la commande :  
```bash
docker-compose up -d
```
Cette commande :  
- Télécharge automatiquement les images manquantes  
- Démarre tous les services définis dans `docker-compose.yml`  

### **4. Vérifier l’état des conteneurs**  
Une fois le déploiement terminé, assurez-vous que tout fonctionne correctement avec :  
```bash
docker ps
```
Les conteneurs suivants doivent être en cours d’exécution :  
- `springboot_container` (Backend)  
- `mysql_container` (Base de données)  
- `phpmyadmin_container` (Interface MySQL)  

## **Accès aux services**  

### **1. Backend Spring Boot**  
Si l’application écoute sur le port **8080**, elle sera accessible via :  
```
http://localhost:8080
```
Consulter les logs si nécessaire :  
```bash
docker logs springboot_container
```

### **2. Base de données MySQL**  
Si un client MySQL est installé, vous pouvez vous connecter avec :  
```bash
mysql -h 127.0.0.1 -P 3306 -u root -p
```
Les identifiants sont définis dans `docker-compose.yml`.

### **3. Interface phpMyAdmin**  
L’interface web de gestion MySQL est accessible ici :  
```
http://localhost:8081
```
Utiliser les identifiants configurés dans `docker-compose.yml`.

## **Gestion des conteneurs**  

### **Arrêter les services**  
Pour arrêter tous les conteneurs :  
```bash
docker-compose down
```

### **Relancer les services**  
Si les conteneurs sont arrêtés, les relancer avec :  
```bash
docker-compose up -d
```

### **Supprimer les conteneurs et volumes**  
Si vous souhaitez tout supprimer, y compris les données MySQL :  
```bash
docker-compose down -v
```

## **Mises à jour à venir**  
- La **Sprint 2** avec de nouvelles fonctionnalités sera disponible prochainement **dans 4 semaines**.  
- Pour récupérer la nouvelle version et reconstruire les services, exécutez :  
  ```bash
  docker pull mohsenfennnira/newtechmindbackend:sprint2
  docker-compose up --build -d
  ```
  Cette commande force la reconstruction des conteneurs pour appliquer toutes les mises à jour.

## **Dépannage**  

### **Vérifier les logs d’un conteneur**  
Si un service ne fonctionne pas correctement, consulter les logs :  
```bash
docker logs <nom_du_conteneur>
```
Exemple :  
```bash
docker logs springboot_container
```

### **Vérifier tous les conteneurs (y compris les arrêtés)**  
```bash
docker ps -a
```

### **Redémarrer un conteneur spécifique**  
```bash
docker restart <nom_du_conteneur>
```

---

## **Conclusion**  
Vous avez maintenant toutes les étapes pour déployer et tester le backend. Suivez les mises à jour et testez régulièrement les nouvelles versions. Si vous rencontrez des problèmes, vérifiez les logs et assurez-vous que tous les conteneurs fonctionnent correctement.
