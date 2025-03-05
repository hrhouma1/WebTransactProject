# Commandes

```sh
docker-compose up --build -d
```

Cette commande permet de :
- **Lancer** les services définis dans le fichier `docker-compose.yml`.
- **Recompiler** les images des services (`--build`).
- **Démarrer** les conteneurs en arrière-plan (`-d`, mode détaché).

- *Si tu veux ajouter un service spécifique, tu peux préciser son nom à la fin de la commande :*

```sh
docker-compose up --build -d nom_du_service
```

-*Si tu travailles avec **Docker Compose V2**, il est recommandé d'utiliser `docker compose` (sans le tiret) :*

```sh
docker compose up --build -d
```
