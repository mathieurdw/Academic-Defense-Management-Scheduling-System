# 🎓 Application de Gestion des Soutenances et Prise de Rendez-Vous

Une application web dynamique développée en **PHP** suivant l'architecture **MVC (Modèle-Vue-Contrôleur)**. Ce projet vise à automatiser et simplifier la planification des soutenances académiques entre étudiants et examinateurs.

---

## 📌 Table des Matières

- [Fonctionnalités](#-fonctionnalités)
- [Architecture du Projet](#-architecture-du-projet)
- [Technologies Utilisées](#-technologies-utilisées)
- [Base de Données](#-base-de-données)
- [Installation et Configuration](#-installation-et-configuration)
- [Auteurs](#-auteurs)

---

## ✨ Fonctionnalités

### 👥 Gestion des Rôles et Utilisateurs
- **Étudiants** : Inscription, consultation des créneaux disponibles et réservation de rendez-vous pour leurs projets.
- **Examinateurs / Enseignants** : Ajout et gestion des créneaux horaires de disponibilité.
- **Administrateurs** : Vue d'ensemble sur l'ensemble des projets, créneaux et rendez-vous.

### 📅 Plannings et Rendez-Vous
- Attribution dynamique de créneaux aux projets.
- Module dédié aux innovations pour évaluer ou consulter facilement les plannings.

---

## 📁 Architecture du Projet

Le projet suit une structure Modèle-Vue-Contrôleur (MVC) claire :

```text
├── app/
│   ├── controllers/      # Contrôleurs (Projet, Creneau, Personne, RendezVous, etc.)
│   ├── models/           # Modèles de données & ORM de base (Model.php, etc.)
│   ├── router/           # Routage de l'application (router1.php)
│   └── views/            # Vues HTML/PHP (Projets, Créneaux, Connexion, etc.)
├── outil/
│   ├── Connexion.php     # Singleton de connexion PDO à la base de données
│   └── projetdb.sql      # Script d'initialisation SQL
├── public/               # Fichiers statiques (CSS, JS, Bootstrap)
└── index.php             # Point d'entrée principal


**ENGLISH VERSION**


# 🎓 Academic Defense Management & Scheduling System

A dynamic web application built in **PHP** following the **MVC (Model-View-Controller)** architecture. This project aims to automate and streamline the scheduling of academic project defenses between students and examiners.

---

## 📌 Table of Contents

* [Features](https://www.google.com/search?q=%23-features)
* [Project Architecture](https://www.google.com/search?q=%23-project-architecture)
* [Tech Stack](https://www.google.com/search?q=%23-tech-stack)
* [Database](https://www.google.com/search?q=%23-database)
* [Installation and Setup](https://www.google.com/search?q=%23-installation-and-setup)
* [Authors](https://www.google.com/search?q=%23-authors)

---

## ✨ Features

### 👥 Role & User Management

* **Students**: Register, view available time slots, and book defense appointments for their projects.
* **Examiners / Professors**: Add, update, and manage their availability slots.
* **Administrators**: Centralized overview of all projects, time slots, and scheduled defenses.

### 📅 Scheduling & Appointments

* Dynamic assignment of time slots to projects.
* Dedicated module to review, assess, and monitor schedules with ease.

---

## 📁 Project Architecture

The project follows a standard Model-View-Controller (MVC) directory structure:

```text
├── app/
│   ├── controllers/      # Controllers (Project, TimeSlot, User, Appointment, etc.)
│   ├── models/           # Data models & base ORM (Model.php, etc.)
│   ├── router/           # Application routing (router1.php)
│   └── views/            # HTML/PHP views (Projects, Slots, Login, etc.)
├── outil/
│   ├── Connexion.php     # PDO database connection singleton
│   └── projetdb.sql      # Database initialization SQL script
├── public/               # Static assets (CSS, JS, Bootstrap)
└── index.php             # Main application entry point
