### Projet 1 : Plateforme de gestion des soutenances

# 🎓 Application de Gestion des Soutenances et Prise de Rendez-Vous

Une application web dynamique développée en **PHP** suivant l'architecture **MVC (Modèle-Vue-Contrôleur)**. Ce projet vise à automatiser et sécuriser l'organisation, la planification des soutenances académiques et la réservation de créneaux entre étudiants, jurys d'examen et administrateurs.

---

## 📌 Table des Matières
- [Fonctionnalités](#-fonctionnalités)
- [Architecture & Sécurité Applicative](#-architecture--sécurité-applicative)
- [Rôle & Contributions Individuelles](#️-rôle--contributions-individuelles)
- [Structure du Projet](#-structure-du-projet)
- [Modélisation de la Base de Données](#-modélisation-de-la-base-de-données)
- [Preuves Visuelles & Captures d'Écran](#-preuves-visuelles--captures-décran)
- [Installation et Configuration](#-installation-et-configuration)
- [Auteurs](#-auteurs)
- [English Version](#-english-version)

---

## ✨ Fonctionnalités

### 👥 Gestion des Rôles et Contrôle d'Accès (RBAC)
- **Étudiants** : Consultation en temps réel des créneaux disponibles, sélection des projets assignés et réservation de rendez-vous de soutenance.
- **Examinateurs / Enseignants** : Création, modification et suivi des plages de disponibilité horaire.
- **Administrateurs** : Supervision globale des comptes utilisateurs, de l'état des projets, des créneaux et des réservations enregistrées.

### 📅 Moteur de Planification & Détection des Conflits
- Affectation dynamique des créneaux aux projets.
- Algorithme de vérification interdisant les doubles réservations simultanées sur un même créneau ou pour un même jury.

---

## 🔒 Architecture & Sécurité Applicative

Développé en appliquant les recommandations de sécurité de l'**OWASP Top 10** :
* **Protection contre les Injections SQL** : Utilisation stricte de l'interface PDO (*PHP Data Objects*) avec requêtes préparées systématiques et liaison sécurisée des paramètres (*parameter binding*). Aucune variable dynamique n'est concaténée aux requêtes SQL.
* **Contrôle d'Accès par Rôles (RBAC)** : Vérification rigoureuse des variables de session sur chaque point d'entrée des contrôleurs. Toute tentative d'accès direct par URL à une ressource non autorisée est interceptée et redirigée par le routeur.
* **Sécurisation des Sessions** : Régénération des identifiants de session lors de l'authentification afin de prévenir le détournement et la fixation de session.
* **Neutralisation des Failles XSS** : Filtrage et échappement contextuel systématique de toutes les données utilisateurs réinjectées dans les vues HTML via `htmlspecialchars()`.

---

## 🛠️ Rôle & Contributions Individuelles

* **Moteur de Routage & Architecture MVC** : Conception et implémentation du routeur principal (`router1.php`), standardisant l'analyse des requêtes HTTP et leur distribution aux contrôleurs appropriés.
* **Modélisation de Données & Couche d'Abstraction** : Modélisation du schéma relationnel en Troisième Forme Normale (3NF) et développement du singleton de connexion à la base de données (`outil/Connexion.php`).
* **Gestion de l'Authentification & des Droits** : Mise en place du module de validation de sessions garantissant l'étanchéité des privilèges entre étudiants, enseignants et administrateurs.
* **Optimisation des Requêtes & Résolution de Bogues** : Écriture et optimisation des requêtes de jointure complexes pour le tableau de bord de réservation ; refactorisation du mécanisme d'allocation pour empêcher les chevauchements horaires.

---

## 📁 Structure du Projet

```text
├── app/
│   ├── controllers/      # Contrôleurs métier (Projet, Creneau, Personne, RendezVous)
│   ├── models/           # Modèles de données & abstraction (Model.php)
│   ├── router/           # Moteur de routage central (router1.php)
│   └── views/            # Vues et gabarits de présentation (HTML / PHP)
├── outil/
│   ├── Connexion.php     # Singleton de connexion PDO
│   └── projetdb.sql      # Script d'initialisation de la base MySQL
├── public/               # Fichiers statiques (CSS, JS, Bootstrap, images)
│   └── images/           # Captures d'écran et schémas d'architecture
└── index.php             # Point d'entrée unique de l'application

```

---

## 🗄️ Modélisation de la Base de Données

Le schéma relationnel repose sur quatre entités centrales liées par des clés étrangères avec intégrité référentielle :

* `personne` : Données de comptes, rôles et mots de passe.
* `projet` : Définition des sujets de soutenance et des groupes associés.
* `creneau` : Plages horaires déclarées par les examinateurs.
* `rendezvous` : Réservations effectives associant un projet, un créneau et les intervenants.

---

## 📸 Preuves Visuelles & Captures d'Écran

| Tableau de bord & Réservation de créneaux | Schéma Relationnel MySQL (3NF) |
| --- | --- |
|  |  |

---

## 🚀 Installation et Configuration

### Prérequis

* PHP 8.1 ou supérieur
* Serveur MySQL 8.0+ ou MariaDB
* Serveur web local (Apache via XAMPP, WAMP ou conteneur Docker)

### Déploiement Local

1. Cloner le dépôt :
```bash
git clone [https://github.com/mathieurdw/Plateforme-de-gestion-des-soutenances.git](https://github.com/mathieurdw/Plateforme-de-gestion-des-soutenances.git)
cd Plateforme-de-gestion-des-soutenances

```


2. Importer la base de données :
```bash
mysql -u root -p < outil/projetdb.sql

```


3. Configurer les identifiants de base de données dans `outil/Connexion.php` :
```php
define('DB_HOST', 'localhost');
define('DB_NAME', 'projetdb');
define('DB_USER', 'root');
define('DB_PASS', '');

```


4. Démarrer le serveur Apache et ouvrir l'application dans le navigateur :
```text
http://localhost/Plateforme-de-gestion-des-soutenances/index.php

```



---

## 👥 Auteurs

* **Mathieu Royer Dacre Wright** ([Profil GitHub](https://www.google.com/search?q=https://github.com/mathieurdw)) - Architecture, Backend & Sécurité
* Collaborateurs de projet académique (UTT)

---

---

# 🌐 English Version

# 🎓 Academic Defense Management & Scheduling System

A dynamic web platform engineered in **PHP** using the **Model-View-Controller (MVC)** architectural pattern. Designed to automate and secure the coordination of academic project defenses between students, evaluation juries, and administrative staff.

---

## 📌 Table of Contents

* [Features](https://www.google.com/search?q=%23-features-1)
* [Security Architecture & Defensive Controls](https://www.google.com/search?q=%23-security-architecture--defensive-controls)
* [My Role & Individual Contributions](https://www.google.com/search?q=%23%EF%B8%8F-my-role--individual-contributions-1)
* [Project Architecture](https://www.google.com/search?q=%23-project-architecture-1)
* [Database Schema](https://www.google.com/search?q=%23-database-schema-1)
* [Screenshots & Visual Evidence](https://www.google.com/search?q=%23-screenshots--visual-evidence-1)
* [Setup & Local Deployment](https://www.google.com/search?q=%23-setup--local-deployment)
* [Authors](https://www.google.com/search?q=%23-authors-1)

---

## ✨ Features

### 👥 Role-Based Access Control (RBAC)

* **Students**: Real-time browsing of open evaluation slots, project selection, and one-click defense booking.
* **Examiners / Professors**: Definition, update, and real-time tracking of personal availability schedules.
* **Administrators**: Centralized oversight dashboard managing users, projects, scheduling allocations, and appointment conflicts.

### 📅 Scheduling Engine & Conflict Prevention

* Dynamic mapping between examiners, candidate project teams, and time intervals.
* Integrated conflict detection logic preventing concurrent double-bookings across shared evaluation panels.

---

## 🔒 Security Architecture & Defensive Controls

Engineered according to **OWASP Top 10** secure coding standards:

* **SQL Injection Mitigation**: Database access is strictly handled via PHP Data Objects (PDO) using prepared statements with parameter binding. No raw SQL query string concatenation is permitted.
* **Granular RBAC**: Strict session state validation across all controller endpoints (`Student`, `Examiner`, `Administrator`). Direct URL tampering is intercepted by the central routing layer.
* **Session Hardening**: Anti-fixation session regeneration upon successful login, combined with server-side validation to block horizontal and vertical privilege escalation.
* **Cross-Site Scripting (XSS) Prevention**: Systematic output escaping (`htmlspecialchars()`) across all HTML/PHP presentation templates.

---

## 🛠️ My Role & Individual Contributions

* **MVC Routing & Core Engine**: Designed and built the central front-controller and application router (`router1.php`), standardizing parameter validation and route dispatching.
* **Relational Modeling & Abstraction**: Developed the 3NF relational schema and created the reusable PDO database connection singleton wrapper (`outil/Connexion.php`).
* **Authentication & RBAC Logic**: Implemented the session validation middleware enforcing role boundaries and secure user authorization across endpoints.
* **Query Optimization & Bug Fixing**: Handled complex database joins for the booking dashboard and refactored scheduling algorithms to eliminate race conditions during concurrent slot reservations.

---

## 📁 Project Architecture

```text
├── app/
│   ├── controllers/      # Application controllers (Projet, Creneau, Personne, RendezVous)
│   ├── models/           # Data access models and ORM logic (Model.php)
│   ├── router/           # Front controller routing engine (router1.php)
│   └── views/            # Presentation templates (HTML / PHP)
├── outil/
│   ├── Connexion.php     # PDO connection singleton
│   └── projetdb.sql      # Database initialization script
├── public/               # Static web assets (CSS, JS, Bootstrap, images)
│   └── images/           # Screenshots and architecture diagrams
└── index.php             # Unified web application entry point

```

---

## 🗄️ Database Schema

Relational model designed around four interconnected entities with strict foreign key constraints:

* `personne`: Authentication records, role flags, and personal details.
* `projet`: Academic defense topic definitions and student team associations.
* `creneau`: Availability time slots published by examiners.
* `rendezvous`: Concrete bookings linking student projects to confirmed examination panels.

---

## 📸 Screenshots & Visual Evidence

| Role Dashboard & Booking Interface | Relational Database Schema (3NF) |
| --- | --- |
|  |  |

---

## 🚀 Setup & Local Deployment

### Prerequisites

* PHP 8.1+
* MySQL 8.0+ or MariaDB
* Local web server environment (Apache via XAMPP, WAMP, or Docker)

### Installation Steps

1. Clone the repository:
```bash
git clone [https://github.com/mathieurdw/Plateforme-de-gestion-des-soutenances.git](https://github.com/mathieurdw/Plateforme-de-gestion-des-soutenances.git)
cd Plateforme-de-gestion-des-soutenances

```


2. Import the database schema:
```bash
mysql -u root -p < outil/projetdb.sql

```


3. Configure database credentials in `outil/Connexion.php`:
```php
define('DB_HOST', 'localhost');
define('DB_NAME', 'projetdb');
define('DB_USER', 'root');
define('DB_PASS', '');

```


4. Start Apache and open the web portal:
```text
http://localhost/Plateforme-de-gestion-des-soutenances/index.php

```

## 👥 Authors

* **Mathieu Royer Dacre Wright** ([GitHub Profile](https://www.google.com/search?q=https://github.com/mathieurdw)) - Architecture, Backend & Security
* Academic project team collaborators (UTT)

