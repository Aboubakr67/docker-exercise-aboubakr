# Exercice Final - Docker

Ce projet illustre la création d'une application web simple avec Node.js, containerisée à l'aide de Docker, et orchestrée avec Docker Compose. L'objectif est de comprendre les concepts fondamentaux de la conteneurisation et de l'orchestration.

---

## 🛠 Fonctionnalités

- **Application Web avec Node.js :** Une application simple avec un point d'entrée accessible sur le port `3000`.
- **Docker :** Conteneurisation de l'application pour un déploiement reproductible.
- **Docker Compose :** Orchestration des services pour simplifier le déploiement.

---

## 📂 Structure du Projet

```
.
├── app
│   ├── server.js          # Point d'entrée de l'application Node.js
│   ├── package.json       # Gestion des dépendances Node.js
│   ├── Dockerfile         # Fichier pour construire l'image Docker
├── docker-compose.yml     # Fichier pour orchestrer les services
```

---

## 🚀 Prérequis

Assurez-vous d'avoir installé les outils suivants avant de commencer :

- [Node.js](https://nodejs.org/) (optionnel, seulement si vous voulez tester localement sans Docker)
- [Docker](https://www.docker.com/)
- [Docker Compose](https://docs.docker.com/compose/)

---

## ⚙️ Installation

1. Clonez le projet sur votre machine locale :

   ```bash
   git clone https://github.com/Aboubakr67/docker-exercice-aboubakr
   ```

2. Rendez-vous dans le répertoire du projet et assurez-vous que les fichiers nécessaires sont présents.

```bash
   cd docker-exercice-aboubakr
```

---

## 🐳 Utilisation avec Docker

### 1️⃣ Construction de l'image Docker

Pour construire l'image Docker, exécutez la commande suivante :

```bash
docker-compose build
```

### 2️⃣ Démarrage du conteneur

Une fois l'image construite, démarrez le conteneur en arrière-plan avec :

```bash
docker-compose up -d
```

### 3️⃣ Vérification

- Vérifiez que le conteneur fonctionne correctement :
  ```bash
  docker ps
  ```
- Accédez à l'application via votre navigateur à l'adresse suivante :  
  [http://localhost:3000](http://localhost:3000)

---

## 🩺 Vérification de la Santé du Conteneur

Un **HEALTHCHECK** est configuré dans le Dockerfile pour surveiller l'état de l'application.  
Pour vérifier l'état de santé du conteneur, utilisez cette commande :

```bash
docker inspect <NOM_DU_CONTENEUR> | grep Health
```

---

## 🛑 Arrêt des Conteneurs

Pour arrêter les conteneurs, exécutez :

```bash
docker-compose down
```

---

## 📂 Fichiers Importants

### `server.js`

Point d'entrée de l'application Node.js, un serveur simple écoutant sur le port `3000`.

### `Dockerfile`

Fichier pour containeriser l'application :

- Basé sur `node:lts-alpine3.20` pour une image légère.
- Configuration d'un `HEALTHCHECK` pour surveiller l'application.

### `docker-compose.yml`

Fichier d'orchestration pour Docker Compose :

- Définit le service principal (`app`).
- Mappe le port 3000 entre l'hôte et le conteneur.
- Synchronise le répertoire local `app` avec le conteneur pour faciliter le développement.

---

## 📝 Notes

- Si des modifications sont apportées à l'application, reconstruisez l'image avec :

  ```bash
  docker-compose build
  ```

- Si vous rencontrez des problèmes, utilisez la commande suivante pour voir les journaux du conteneur :
  ```bash
  docker-compose logs
  ```

---

## 📜 Licence

Ce projet est sous licence MIT. Consultez le fichier [LICENSE](LICENSE) pour plus de détails.
