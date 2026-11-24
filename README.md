\# TP4 : Docker et Docker Compose – Déploiement d'une application MERN



\## 1. Objectif du TP



L'objectif de ce TP est de conteneuriser une application MERN (MongoDB, Express, React et Node.js) à l'aide de Docker, puis d'utiliser Docker Compose pour orchestrer les différents services.



\## 2. Structure du projet



Le projet est organisé comme suit :



\- `Client/` : application frontend React.

\- `Server/` : application backend Node.js.

\- `docker-compose.yml` : fichier de configuration des services Docker.



\## 3. Création des Dockerfiles



Deux Dockerfiles ont été créés :



\- \*\*Server/Dockerfile\*\* : permet de construire l'image du serveur Node.js.

\- \*\*Client/Dockerfile\*\* : permet de construire l'image du frontend React et de servir les fichiers générés après le build.



Les deux images utilisent `node:lts-alpine`.



\## 4. Création du réseau Docker



Un réseau Docker nommé `mern-network` a été configuré pour permettre la communication entre les conteneurs.



\## 5. Configuration de Docker Compose



Le fichier `docker-compose.yml` définit trois services :



\- \*\*mongodb\*\* : base de données MongoDB.

\- \*\*server\*\* : serveur backend accessible sur le port 9000.

\- \*\*client\*\* : application frontend accessible sur le port 3000.



La variable d'environnement `MONGO\_URI` permet de définir l'adresse de connexion à MongoDB.



\## 6. Lancement de l'application



Pour construire les images et démarrer les trois services, exécuter la commande :



```bash

docker compose up --build

```



Pour vérifier l'état des conteneurs :



```bash

docker compose ps

```



Pour consulter les journaux :



```bash

docker compose logs

```



\## 7. Accès à l'application



Après le démarrage des conteneurs :



\- Frontend : http://localhost:3000

\- Backend : http://localhost:9000

\- MongoDB : port 27017



\## 8. Arrêt des conteneurs



Pour arrêter les services, exécuter :



```bash

docker compose down

```



\## 9. Conclusion



Ce TP a permis de découvrir la conteneurisation d'une application MERN avec Docker et l'orchestration de plusieurs services avec Docker Compose. Les services MongoDB, Server et Client ont été configurés et démarrés dans des conteneurs distincts.

