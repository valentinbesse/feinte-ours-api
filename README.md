# 🧸 Feinte de l’Ours - API Django

Ce projet est l’API backend du site de [l'association La Feinte de l’Ours](http://lafeintedelours.fr/), une communauté autour du jeu de société.  
L’objectif est de gérer les adhérents, les bénévoles, les formations, les droits d’accès, et les postes.

---

## 🚀 Technologies utilisées

- [Python 3.10+](https://www.python.org/)
- [Django](https://www.djangoproject.com/)
- [Django REST Framework](https://www.django-rest-framework.org/)
- SQLite (par défaut pour dev)

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

## 🤝 Contribuer

Ce projet est en phase d’apprentissage. Les suggestions sont les bienvenues via Issues ou Pull Requests.