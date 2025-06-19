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

### .gitlab-ci.yml

- Utilise l’image Docker willhallonline/ansible:latest, qui contient Ansible préinstallé.
- Utilise un runner taggé Debian-Runner.
- Crée le dossier .ssh, puis :
  . injecte la clé SSH privée stockée dans la variable GitLab SSHKEY,
  . la rend utilisable (droits 600).
- Exécute le playbook 01-Deploy-Zabbix-docker.yml pour déployer Zabbix via Ansible.
- Le job est en mode manuel (when: manual), donc il ne s’exécute que si on clique sur "Play" dans l’interface GitLab CI.
