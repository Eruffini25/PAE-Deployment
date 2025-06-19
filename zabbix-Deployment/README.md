# Zabbix deployment

## Expliquation Script

### 01-Deploy-Zabbix-docker.yml

- Crée le dossier /srv/zabbix pour stocker la configuration.
- Génère un fichier docker-compose.yml avec :
  . un conteneur PostgreSQL pour la base de données,
  . un serveur Zabbix,
  . une interface web Zabbix (accessible sur le port 8081).
- Lance les conteneurs via Docker Compose v2.
- Affiche dans la console l’URL et les identifiants par défaut :
  . http://<ip>:8081
  . Login : Admin
  . Mot de passe : zabbix
- Attend automatiquement que l’interface web soit disponible, avec 10 tentatives espacées de 10 secondes.

