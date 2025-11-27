# Minetest-server
<div align="center">
  
# 🚀 LuantiServer

**Solution complète d'hébergement et d'administration pour serveur Minecraft/Luanti avec sécurité renforcée**

[![Linux](https://img.shields.io/badge/Linux-Ubuntu-orange?logo=ubuntu)](https://ubuntu.com/)
[![Security](https://img.shields.io/badge/Security-Hardened-green?logo=shieldsdotio)](https://github.com)
[![License](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)

[Fonctionnalités](#-fonctionnalités) • [Technologies](#-technologies) • [Installation](#-installation) • [Sécurité](#-sécurité) • [Contribution](#-contribution)

</div>

---

## 📋 À propos du projet

**LuantiServer** est une plateforme d'hébergement et d'administration de serveur Minecraft/Luanti conçue pour offrir une expérience de jeu sécurisée, stable et facilement administrable. Le projet intègre une gestion multi-mondes, une interface web de monitoring et des mesures de cybersécurité avancées.

L'objectif principal est de proposer une solution robuste pour héberger plusieurs mondes de jeu avec des configurations distinctes, tout en protégeant efficacement les joueurs contre les menaces courantes.

---

## ✨ Fonctionnalités

### 🌍 Hébergement Multi-Mondes
- **Vanilla** : Expérience Minecraft classique
- **Créatif** : Mode construction illimitée
- **Exploration** : Découverte d'environnements générés
- **Survie** : Défi traditionnel de survie
- **Monde personnalisé** : Configuration sur mesure

Chaque monde dispose de sa propre configuration, permettant une personnalisation poussée des règles de jeu, des plugins et des paramètres serveur.

### 🖥️ Interface Web Sécurisée
- Dashboard de monitoring en temps réel
- Statistiques détaillées par monde (joueurs connectés, performances, utilisation ressources)
- Supervision de l'état de santé du serveur et des services
- Accès sécurisé via SSL/TLS

### 🤖 Scripting & Automatisation
- Scripts Bash et Python pour l'administration simplifiée
- Gestion automatisée des backups
- Démarrage/arrêt des mondes
- Maintenance et mises à jour facilitées

### 🔒 Cybersécurité Renforcée
- Protection contre les attaques par force brute sur les comptes joueurs
- Durcissement de la configuration système
- Surveillance et limitation des tentatives d'authentification
- Gestion des accès et des permissions
- Logs centralisés et monitoring de sécurité

---

## 🛠️ Technologies

| Catégorie | Technologies |
|-----------|--------------|
| **Serveur de jeu** | Minecraft Server, Luanti |
| **Système d'exploitation** | Linux (Ubuntu Server) |
| **Scripting** | Bash, Python 3 |
| **Sécurité** | SSL/TLS, Fail2ban, UFW |
| **Web** | NGINX, Dashboard web custom |
| **Monitoring** | Scripts de supervision personnalisés |

---

## 🚀 Installation

### Prérequis

- Ubuntu Server 20.04+ (ou distribution Linux compatible)
- Python 3.8+
- Accès root ou sudo
- Ports 25565 (Minecraft) et 443 (HTTPS) disponibles

### Étapes d'installation


