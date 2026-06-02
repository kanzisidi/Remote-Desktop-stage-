# 🖥️ Plateforme de Streaming de Bureau à Distance

Ce projet est une solution complète de monitoring et de pilotage à distance. Il permet de surveiller les ressources d'une machine cible en temps réel et de la contrôler via une infrastructure distribuée. 

Ce projet est réalisé dans le cadre d'un stage de développement de 2 mois.

---

## 🏗️ Architecture du Projet

Le système repose sur une architecture centralisée autour d'un serveur d'orchestration, faisant le pont entre la machine cible et les interfaces de contrôle. L'infrastructure est divisée en 4 composants distincts :

1. **Agent Système (`/agent`) - C**
   * Programme bas-niveau s'exécutant sur la machine cible.
   * Rôle : Récolte des métriques système (CPU, RAM), capture d'écran, et exécution des commandes locales.
2. **Serveur d'Orchestration (`/server`) - Go (Golang)**
   * Le cœur central du système.
   * Rôle : Routage des messages en temps réel via WebSockets, gestion des connexions clients et agents, et exposition de l'API.
3. **Dashboard Web (`/dashboard`) - JavaScript / HTML / CSS**
   * Interface de visualisation légère.
   * Rôle : Affichage en temps réel des métriques et de l'état de la machine cible depuis un navigateur web.
4. **Client de Pilotage (`/client`) - C# (.NET)**
   * Application de bureau native.
   * Rôle : Interface de contrôle avancé permettant d'envoyer des commandes d'exécution à distance à la machine cible.

---

## 🛠️ Prérequis

Pour compiler et exécuter l'ensemble du projet, les outils suivants sont nécessaires :

* **C :** Compilateur GCC ou équivalent (MinGW sur Windows).
* **Go :** [Go 1.20+](https://go.dev/dl/)
* **C# :** [SDK .NET 7.0+](https://dotnet.microsoft.com/download) et Visual Studio (ou Rider).
* **JS :** Un navigateur web moderne (aucun framework lourd n'est requis au lancement).

---

## 🚀 Installation et Démarrage

### 1. Démarrer le Serveur (Go)
```bash
cd server
go run main.go