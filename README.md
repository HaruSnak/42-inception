<img src="readme/inception.png" alt="inception" width="900"/>

<div align="center">

# Inception
### A Docker Infrastructure Project at 42 School

[![Contributors][contributors-shield]][contributors-url]
[![Forks][forks-shield]][forks-url]
[![Stargazers][stars-shield]][stars-url]
[![Issues][issues-shield]][issues-url]
[![License][license-shield]][license-url]

</div>

---

## 🇬🇧 English

<details>
<summary><b>📖 Click to expand/collapse English version</b></summary>

### 📖 About

**Inception** is a compulsory project for 42 School students. It consists of setting up a complete multi-service infrastructure using Docker Compose, NGINX with TLS, WordPress with php-fpm, and MariaDB, all configured from scratch following best practices.

This project teaches:
- Docker containerization and orchestration
- Web server configuration with SSL/TLS
- Database management and security
- WordPress deployment and configuration
- Network isolation and volume persistence
- System administration skills

### 🧠 Skills Learned

By completing the Inception project, students develop essential skills in system administration and DevOps:

- **Docker usage**: Building custom images, managing containers, and using Docker Compose for orchestration.
- **NGINX configuration**: Setting up reverse proxy, SSL/TLS encryption, and security headers.
- **WordPress deployment**: Installing and configuring WordPress with php-fpm, using WP-CLI.
- **MariaDB setup**: Database initialization, user management, and secure connections.
- **Volume management**: Persisting data with Docker volumes on the host filesystem.
- **Network security**: Isolated networks, port management, and access control.
- **Environment variables**: Managing configuration with .env files and secrets.
- **Best practices**: Following Docker and security best practices, proper daemon management.

## Approach
The Inception project challenged me to build a complete infrastructure from the ground up. I focused on creating a secure, scalable setup with proper separation of concerns. The architecture uses NGINX as the entry point with TLS encryption, WordPress for the application layer, and MariaDB for data persistence, all orchestrated with Docker Compose.

I implemented custom Dockerfiles for each service, ensuring no pre-built images were used, and configured everything to run in foreground mode for proper signal handling. Security was a priority, with TLS 1.2/1.3 only, environment variables for secrets, and isolated networks.

The setup includes automated initialization scripts, volume persistence, and comprehensive error handling. This project demonstrates real-world system administration skills applicable to modern DevOps practices.

### **Features**

**Custom Docker Images:** All services built from Debian Bullseye without using DockerHub pre-built images.

**TLS Encryption:** NGINX configured with self-signed SSL certificates supporting only TLS 1.2 and 1.3.

**WordPress Integration:** Automated installation and configuration using WP-CLI, with two user accounts.

**Database Security:** MariaDB with secure user management, root password protection, and isolated access.

**Volume Persistence:** Data stored on host at /home/haru/data/ for both WordPress files and database.

**Network Isolation:** All services communicate on a custom bridge network, with NGINX as the sole entry point.

### **Additional Features:**

**Auto-restart:** Containers configured to restart automatically on crash.

**Security Headers:** X-Frame-Options, X-Content-Type-Options, X-XSS-Protection in NGINX.

**Static File Caching:** Optimized caching for CSS, JS, and images.

**Environment Variables:** All sensitive data managed through .env file and secrets.

### 📋 Table of Contents

- [Features](#features)
- [Installation](#installation)
- [Usage](#usage)
- [Project Structure](#project-structure)
- [Testing](#testing)
- [Credits](#credits)

<a name="features"></a>

### ✨ Features

- **Complete infrastructure** with NGINX, WordPress, and MariaDB
- **TLS 1.2/1.3 encryption** with self-signed certificates
- **Custom Docker images** built from Debian Bullseye
- **Volume persistence** for data durability
- **Isolated network** for secure inter-container communication
- **Automated setup** with Docker Compose and initialization scripts
- **Security best practices** with environment variables and secrets

<a name="installation"></a>

### 🚀 Installation

```bash
# Clone the repository
git clone https://github.com/HaruSnak/42-inception
cd 42-inception

# Configure domain in /etc/hosts
sudo bash srcs/requirements/tools/setup_hosts.sh

# Build and start services
make all
```

### Environment Variables
The `.env` file in `srcs/` contains all configuration:
```env
DOMAIN_NAME=haru.42.fr
MYSQL_ROOT_PASSWORD=rootpassword123
MYSQL_DATABASE=wordpress
MYSQL_USER=wpuser
MYSQL_PASSWORD=userpassword123
WP_ADMIN_USER=webmaster
WP_ADMIN_PASSWORD=adminpass123
WP_ADMIN_EMAIL=webmaster@haru.42.fr
WP_USER=normaluser
WP_USER_EMAIL=user@haru.42.fr
WP_USER_PASSWORD=userpass123
```

<a name="usage"></a>

### 💻 Usage

Access WordPress at https://haru.42.fr (accept self-signed certificate warning).

Admin login: webmaster / adminpass123

### 📂 Project Structure

```
42-inception/
├── Makefile                    # Build script
├── README.md                   # This file
├── README-Template.md          # Template for README
├── srcs/
│   ├── .env                    # Environment variables
│   ├── docker-compose.yml      # Service orchestration
│   └── requirements/
│       ├── mariadb/
│       │   ├── Dockerfile
│       │   ├── conf/
│       │   └── tools/
│       ├── nginx/
│       │   ├── Dockerfile
│       │   ├── conf/
│       │   └── tools/
│       └── wordpress/
│           ├── Dockerfile
│           ├── conf/
│           └── tools/
└── secrets/                    # Sensitive credentials
```

<a name="testing"></a>

### 🧪 Testing

```bash
# Check containers
docker ps

# View logs
make logs

# Test HTTPS
curl -k https://haru.42.fr
```

### 👨‍🎓 Note
<p align="left">
    <img src="https://image.noelshack.com/fichiers/2024/11/2/1710273269-100.png"
         alt="100/100" width="180" height="184">
</p>

<a name="credits"></a>

### 📖 Credits

- **42 School**: Curriculum project
- **Docker Documentation**: [docs.docker.com](https://docs.docker.com/)
- **NGINX Docs**: [nginx.org](https://nginx.org/en/docs/)
- **WordPress CLI**: [wp-cli.org](https://wp-cli.org/)
- **MariaDB Docs**: [mariadb.org](https://mariadb.org/documentation/)

### 📄 License

This project is licensed under the **MIT License**.

</details>

---

## 🇫🇷 Français

<details>
<summary><b>📖 Cliquez pour développer/réduire la version française</b></summary>

### 📖 À propos

**Inception** est un projet obligatoire pour les étudiants de l'école 42. Il consiste à mettre en place une infrastructure multi-services complète utilisant Docker Compose, NGINX avec TLS, WordPress avec php-fpm et MariaDB, tout configuré à partir de zéro en suivant les meilleures pratiques.

Ce projet enseigne :
- La conteneurisation et l'orchestration Docker
- La configuration de serveur web avec SSL/TLS
- La gestion et la sécurité des bases de données
- Le déploiement et la configuration de WordPress
- L'isolation réseau et la persistance des volumes
- Les compétences en administration système

### 🧠 Compétences acquises

En complétant le projet Inception, les étudiants développent des compétences essentielles en administration système et DevOps :

- **Utilisation de Docker** : Construction d'images personnalisées, gestion des conteneurs et utilisation de Docker Compose pour l'orchestration.
- **Configuration NGINX** : Mise en place de proxy inverse, chiffrement SSL/TLS et en-têtes de sécurité.
- **Déploiement WordPress** : Installation et configuration de WordPress avec php-fpm, utilisant WP-CLI.
- **Configuration MariaDB** : Initialisation de base de données, gestion des utilisateurs et connexions sécurisées.
- **Gestion des volumes** : Persistance des données avec des volumes Docker sur le système de fichiers hôte.
- **Sécurité réseau** : Réseaux isolés, gestion des ports et contrôle d'accès.
- **Variables d'environnement** : Gestion de la configuration avec des fichiers .env et secrets.
- **Meilleures pratiques** : Suivre les meilleures pratiques Docker et de sécurité, gestion appropriée des démons.

## Approche
Le projet Inception m'a défié à construire une infrastructure complète à partir de zéro. Je me suis concentré sur la création d'une configuration sécurisée et évolutive avec une séparation appropriée des préoccupations. L'architecture utilise NGINX comme point d'entrée avec chiffrement TLS, WordPress pour la couche application et MariaDB pour la persistance des données, le tout orchestré avec Docker Compose.

J'ai implémenté des Dockerfiles personnalisés pour chaque service, en m'assurant qu'aucune image pré-construite n'était utilisée, et configuré tout pour fonctionner en mode avant-plan pour une gestion appropriée des signaux. La sécurité était une priorité, avec TLS 1.2/1.3 uniquement, variables d'environnement pour les secrets et réseaux isolés.

La configuration inclut des scripts d'initialisation automatisés, persistance des volumes et gestion d'erreurs complète. Ce projet démontre des compétences en administration système du monde réel applicables aux pratiques DevOps modernes.

### **Fonctionnalités**

**Images Docker personnalisées :** Tous les services construits à partir de Debian Bullseye sans utiliser d'images pré-construites DockerHub.

**Chiffrement TLS :** NGINX configuré avec certificats SSL auto-signés ne supportant que TLS 1.2 et 1.3.

**Intégration WordPress :** Installation et configuration automatisées utilisant WP-CLI, avec deux comptes utilisateurs.

**Sécurité de base de données :** MariaDB avec gestion sécurisée des utilisateurs, protection du mot de passe root et accès isolé.

**Persistance des volumes :** Données stockées sur l'hôte à /home/haru/data/ pour les fichiers WordPress et la base de données.

**Isolation réseau :** Tous les services communiquent sur un réseau bridge personnalisé, avec NGINX comme seul point d'entrée.

### **Fonctionnalités supplémentaires :**

**Redémarrage automatique :** Conteneurs configurés pour redémarrer automatiquement en cas de crash.

**En-têtes de sécurité :** X-Frame-Options, X-Content-Type-Options, X-XSS-Protection dans NGINX.

**Cache de fichiers statiques :** Cache optimisé pour CSS, JS et images.

**Variables d'environnement :** Toutes les données sensibles gérées via fichier .env et secrets.

### 📋 Table des matières

- [Caractéristiques](#caractéristiques)
- [Installation](#installation-1)
- [Utilisation](#utilisation)
- [Structure du projet](#structure-du-projet)
- [Test](#test)
- [Crédits](#crédits-1)

<a name="caractéristiques"></a>

### ✨ Caractéristiques

- **Infrastructure complète** avec NGINX, WordPress et MariaDB
- **Chiffrement TLS 1.2/1.3** avec certificats auto-signés
- **Images Docker personnalisées** construites à partir de Debian Bullseye
- **Persistance des volumes** pour la durabilité des données
- **Réseau isolé** pour une communication inter-conteneurs sécurisée
- **Configuration automatisée** avec Docker Compose et scripts d'initialisation
- **Meilleures pratiques de sécurité** avec variables d'environnement et secrets

<a name="installation-1"></a>

### 🚀 Installation

```bash
# Cloner le dépôt
git clone https://github.com/HaruSnak/42-inception
cd 42-inception

# Configurer le domaine dans /etc/hosts
sudo bash srcs/requirements/tools/setup_hosts.sh

# Construire et démarrer les services
make all
```

### Variables d'environnement
Le fichier `.env` dans `srcs/` contient toute la configuration :
```env
DOMAIN_NAME=haru.42.fr
MYSQL_ROOT_PASSWORD=rootpassword123
MYSQL_DATABASE=wordpress
MYSQL_USER=wpuser
MYSQL_PASSWORD=userpassword123
WP_ADMIN_USER=webmaster
WP_ADMIN_PASSWORD=adminpass123
WP_ADMIN_EMAIL=webmaster@haru.42.fr
WP_USER=normaluser
WP_USER_EMAIL=user@haru.42.fr
WP_USER_PASSWORD=userpass123
```

<a name="utilisation"></a>

### 💻 Utilisation

Accédez à WordPress sur https://haru.42.fr (acceptez l'avertissement de certificat auto-signé).

Connexion admin : webmaster / adminpass123

<a name="structure-du-projet"></a>

### 📂 Structure du projet

```
42-inception/
├── Makefile                    # Script de build
├── README.md                   # Ce fichier
├── README-Template.md          # Template pour README
├── srcs/
│   ├── .env                    # Variables d'environnement
│   ├── docker-compose.yml      # Orchestration des services
│   └── requirements/
│       ├── mariadb/
│       │   ├── Dockerfile
│       │   ├── conf/
│       │   └── tools/
│       ├── nginx/
│       │   ├── Dockerfile
│       │   ├── conf/
│       │   └── tools/
│       └── wordpress/
│           ├── Dockerfile
│           ├── conf/
│           └── tools/
└── secrets/                    # Identifiants sensibles
```

<a name="test"></a>

### 🧪 Test

```bash
# Vérifier les conteneurs
docker ps

# Voir les logs
make logs

# Tester HTTPS
curl -k https://haru.42.fr
```

### 👨‍🎓 Note
<p align="left">
    <img src="https://image.noelshack.com/fichiers/2024/11/2/1710273269-100.png"
         alt="100/100" width="180" height="184">
</p>

<a name="crédits-1"></a>

### 📖 Crédits

- **École 42** : Projet du curriculum
- **Documentation Docker** : [docs.docker.com](https://docs.docker.com/)
- **Docs NGINX** : [nginx.org](https://nginx.org/en/docs/)
- **WordPress CLI** : [wp-cli.org](https://wp-cli.org/)
- **Docs MariaDB** : [mariadb.org](https://mariadb.org/documentation/)

### 📄 Licence

Ce projet est sous licence **MIT**.

</details>

---

[contributors-shield]: https://img.shields.io/github/contributors/HaruSnak/42-inception.svg?style=for-the-badge
[contributors-url]: https://github.com/HaruSnak/42-inception/graphs/contributors
[forks-shield]: https://img.shields.io/github/forks/HaruSnak/42-inception.svg?style=for-the-badge
[forks-url]: https://github.com/HaruSnak/42-inception/network/members
[stars-shield]: https://img.shields.io/github/stars/HaruSnak/42-inception.svg?style=for-the-badge
[stars-url]: https://github.com/HaruSnak/42-inception/stargazers
[issues-shield]: https://img.shields.io/github/issues/HaruSnak/42-inception.svg?style=for-the-badge
[issues-url]: https://github.com/HaruSnak/42-inception/issues
[linkedin-shield]: https://img.shields.io/badge/-LinkedIn-black.svg?style=for-the-badge&logo=linkedin&colorB=555
[linkedin-url]: https://www.linkedin.com/in/shany-moreno-5a863b2aa
[license-shield]: https://img.shields.io/github/license/HaruSnak/42-inception.svg?style=for-the-badge
[license-url]: https://github.com/HaruSnak/42-inception/blob/master/LICENSE
