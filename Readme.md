# 🎢 Application Web - Gestion d'un Parc de Jeux

Ce projet est une application web développée en PHP natif (architecture MVC) permettant la gestion centralisée d'un parc de jeux (jeux, responsables, clients, réservations, finances). 

Projet réalisé dans le cadre de la formation IDSD (EST Nador).

## 📁 Architecture du Projet (MVC)

Le projet utilise une architecture **Public / Privé** pour garantir la sécurité des données. Le code métier est isolé et seul le dossier `public` est accessible via le navigateur.

### 🔒 `/backend` (Le Moteur - Accès restreint)
Ce dossier contient toute la logique de l'application. Il ne doit **jamais** être accessible directement via une URL.
* **`/config`** : Fichiers de configuration globale. Contient `database.php` qui gère la connexion sécurisée à MySQL via PDO.
* **`/models`** : Le **M** de MVC. Contient les requêtes SQL (ex: `jeu_model.php`, `user_model.php`). C'est ici qu'on interagit avec la base de données.
* **`/controllers`** : Le **C** de MVC. C'est le cerveau de l'application. Les contrôleurs traitent les données envoyées par l'utilisateur, font appel aux modèles, et chargent les vues correspondantes.
* **`/views`** : Le **V** de MVC. Contient les interfaces graphiques (fichiers HTML/PHP) basées sur le template SB Admin.
* **`/helpers`** : Contient des fonctions utilitaires réutilisables partout dans le projet (ex: formatage des dates, nettoyage des données, gestion des messages flash).

### 🗄️ `/database` (Données)
* Contient le fichier `schema.sql`. Ce script contient la structure complète de la base de données (MLD/MCD) pour initialiser le projet facilement sur un serveur local ou phpMyAdmin.

### 🌐 `/public` (La Vitrine - Point d'entrée)
C'est le **seul** dossier exposé au navigateur web. L'URL du projet doit toujours pointer ici.
* **`index.php`** : Le Routeur (Front Controller). C'est la porte d'entrée unique de l'application. Il lit l'URL et redirige le visiteur vers le bon contrôleur dans le backend.
* **`/assets`** : Contient toutes les ressources statiques du design (fichiers `.css`, scripts `.js`, images, polices).

### ⚙️ Fichiers à la racine
* **`.env`** : Fichier ultra-secret contenant les identifiants de la base de données (Host, DB Name, User, Password). **Attention : Ne jamais le pousser sur GitHub.**
* **`.gitignore`** : Liste des fichiers que Git doit ignorer (comme `.env` ou les dossiers temporaires) pour éviter les fuites de sécurité et les conflits.

## 🚀 Installation locale (XAMPP / WAMP)

1. Cloner ce dépôt dans le dossier `htdocs` (XAMPP) ou `www` (WAMP).
2. Créer une base de données sur phpMyAdmin et importer le fichier `/database/schema.sql`.
3. Créer un fichier `.env` à la racine (basé sur un éventuel `.env.example`) et y mettre vos identifiants MySQL locaux.
4. Accéder à l'application via votre navigateur : `http://localhost/Parc_de_jeux/public/`