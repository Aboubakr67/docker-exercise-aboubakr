# Image légère de Node.js basée sur Alpine Linux
FROM node:lts-alpine3.20

# Répertoire de travail dans le conteneur
WORKDIR /usr/src/app

# Copie uniquement le fichier package.json dans le conteneur pour installer les dépendances
COPY package.json ./

# Installe les dépendances définies dans le fichier package.json
RUN npm install

# Copier le reste des fichiers de l'application dans le conteneur
COPY . .

# Exposer le port 3000
EXPOSE 3000

# Ajoute un HEALTHCHECK pour surveiller l'état de l'application
# - Vérifie toutes les 30 secondes (interval=30s)
# - Considère que la vérification échoue si aucune réponse n'est reçue sous 5 secondes (timeout=5s)
# - Attend 15 secondes avant d'effectuer la première vérification (start-period=15s)
# - Déclare l'application comme "en panne" après 3 échecs consécutifs (retries=3)
HEALTHCHECK --interval=30s --timeout=5s --start-period=15s --retries=3 \
    CMD curl -f http://localhost:3000/ || exit 1

# Commande pour démarrer l'application
CMD ["npm", "start"]
