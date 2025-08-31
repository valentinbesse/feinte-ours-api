# 🧸 Feinte de l’Ours - API Django

Ce projet est l’API backend du site de [l'association La Feinte de l’Ours](http://lafeintedelours.fr/), une communauté autour du jeu de société.  
L’objectif est de gérer les adhérents, les bénévoles, les formations, les droits d’accès, et les postes.

---

## 🚀 Technologies utilisées

- [Python 3.10+](https://www.python.org/)
- [Django](https://www.djangoproject.com/) – Framework web principal
- [Django REST Framework](https://www.django-rest-framework.org/) – Création d’API RESTful
- [MongoDB](https://www.mongodb.com/) – Base de données NoSQL
- [Djongo](https://www.djongomapper.com/) – Connecteur Django ↔ MongoDB
- [Docker](https://www.docker.com/) & [Docker Compose](https://docs.docker.com/compose/) – Conteneurisation et orchestration

---

## 🤔 Pourquoi ces choix ?

- **Python & Django** : un écosystème mature et robuste, idéal pour un développement rapide et maintenable, en cohérence avec les pratiques de **Software Craftsmanship**.  
- **Django REST Framework** : une solution éprouvée pour concevoir des API RESTful lisibles, documentées et testables.  
- **MongoDB (NoSQL)** : apporte la flexibilité nécessaire pour modéliser des données hétérogènes (adhérents, bénévoles, rôles, droits) sans rigidité relationnelle.  
- **Djongo** : permet d’utiliser MongoDB avec l’ORM Django, ce qui conserve les bonnes pratiques Django tout en profitant du NoSQL.  
- **Docker & Compose** : garantissent une reproductibilité de l’environnement (base de données, services) et facilitent le déploiement.  
- **TDD & BDD** : l’approche de développement guidée par les tests et par le métier assure un code fiable, simple et aligné avec les besoins réels de l’association.

---

## 📦 Installation locale (macOS/Linux)

### 1. Cloner le projet

```bash
git clone https://github.com/<ton-nom-utilisateur>/feinte-ours.git
cd feinte-ours
```

### 2. Créer un environnement virtuel

```bash
python3 -m venv venv
source venv/bin/activate
```

### 3. Installer les dépendances

```bash
pip install -r requirements.txt
```

### 4. Appliquer les migrations

```bash
python manage.py migrate
```

### 5. Lancer le serveur de développement

```bash
python manage.py runserver
```

Visite ensuite http://127.0.0.1:8000

## 🛠️ Fonctionnalités prévues

- Gestion des utilisateurs (adhérents, bénévoles)
- Adhésions annuelles
- Formations et suivi
- Rôles, postes et droits d'accès
- Authentification via JWT

## 🧭 Philosophie & Organisation du Projet

### Principes utilisés

- **Software Craftsmanship**  
  Le projet respecte les bonnes pratiques de lisibilité, maintenabilité et modularité.  
  Chaque domaine métier (adhérents, bénévoles, formations…) est implémenté comme une **app Django indépendante**, ce qui permet une meilleure isolation et testabilité.

- **Test Driven Development (TDD)**  
  Chaque nouvelle fonctionnalité est développée en commençant par les tests unitaires.  
  Les tests se trouvent directement dans les apps (`apps/*/tests/`) pour rester proches du code, et des tests d’intégration sont regroupés dans `tests/`.

- **Business Driven Development (BDD)**  
  La logique métier est décrite sous forme de **scénarios lisibles** par les non-développeurs (fichiers `.feature`).  
  Ces scénarios vivent dans `tests/features/` (globaux) ou dans chaque app (`apps/*/tests/features/`).  
  Cela permet de vérifier que l’application répond aux besoins réels de l’association.

- **MongoDB via Docker**  
  La base de données est hébergée via un conteneur Docker, isolée du code.  
  Des scripts d’initialisation (`docker/mongo-init.js`) permettent de préparer la base au premier démarrage.

---

### Organisation du répertoire

``` text
feinte-ours-api/
├── apps/ # Applications Django (modules métier)
│ ├── members/ # Gestion des adhérents
│ │ ├── services/ # Logique métier
│ │ ├── repositories/ # Accès MongoDB (ODM / requêtes)
│ │ └── tests/ # Tests unitaires + scénarios BDD
│ └── volunteers/ # Gestion des bénévoles
│
├── config/ # Paramétrage du projet Django
│ ├── settings/ # Base, Dev, Prod
│ └── urls.py, wsgi.py
│
├── tests/ # Tests globaux (intégration, end-to-end, BDD)
│ ├── factories/ # Génération d’objets de test
│ └── features/ # Scénarios BDD globaux
│
├── docker/ # Configuration Docker (API + MongoDB)
│ ├── docker-compose.yml
│ ├── Dockerfile
│ └── mongo-init.js
│
├── requirements/ # Dépendances (base, dev, prod)
├── scripts/ # Scripts utilitaires (reset DB, fixtures, etc.)
├── manage.py
└── .env
```

### Règles générales
- **Une app = un domaine métier** → séparation claire.  
- **`services/`** → logique métier indépendante des modèles.  
- **`repositories/`** → interactions avec la base MongoDB.  
- **Tests proches du code + répertoire global `tests/`** pour la cohérence TDD/BDD.  
- **Config centralisée dans `config/`** → facile à déployer en dev, staging, prod.  


## 🤝 Contribuer

Ce projet est en phase d’apprentissage. Les suggestions sont les bienvenues via Issues ou Pull Requests.