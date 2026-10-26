# Rapport de stage d'été : Mise en œuvre de la solution iTop

Rapport de stage réalisé dans le cadre d'un projet mené avec l'Agence de Promotion de l'Industrie et de l'Innovation (APII), à l'Université Internationale de Tunis (UIT).

**Étudiant :** Malek Addali
**Encadrant :** Anwer Gnaoui
**Année universitaire :** 2025-2026

## Objet du projet

Mise en place d'une plateforme de gestion des services informatiques (ITSM) basée sur l'outil [iTop](https://www.combodo.com/itop) (Combodo), dans un environnement de test sous Windows, avec la suite XAMPP (Apache, PHP, MariaDB). Le projet permet d'expérimenter les processus ITIL et la gestion de la CMDB.

## Contenu du dépôt
├── main.tex # Fichier principal (préambule et assemblage)
├── pagedegarde.tex # Page de garde
├── content.tex # Table des matières
├── introductionG.tex # Introduction
├── chapitre1.tex # Présentation du projet
├── chapitre2.tex # Présentation d’iTop / Combodo
├── chapitre3.tex # Environnement et technologies utilisés
├── chapitre4.tex # Installation et configuration d’iTop sous Windows
├── chapitre5.tex # Difficultés rencontrées et solutions
├── conclusionG.tex # Conclusion, perspectives et ouverture
├── images/ # Captures d’écran et schémas (image1.png à image16.png)
├── presentation_itop/ # Présentation HTML d’iTop
└── .gitignore # Fichiers temporaires LaTeX exclus du dépôt
## Installation d'iTop sous Windows

### Prérequis

- Windows 10 ou 11
- Un navigateur web

### Étape 1 : Installer XAMPP

1. Télécharge XAMPP depuis le site officiel d'Apache Friends.
2. Lance l'installateur et installe XAMPP, par exemple dans `C:\xampp`.
3. Ouvre le **XAMPP Control Panel** et démarre les services **Apache** et **MySQL**.

### Étape 2 : Télécharger et préparer iTop

1. Télécharge iTop Community depuis SourceForge.
2. Décompresse l'archive ZIP. Tu obtiens un dossier `web` qui contient notamment `index.php`, `conf/`, `env-production/`, `setup/`, `pages/` et `application/`.
3. Renomme le dossier `web` en `itop`.
4. Copie le dossier `itop` dans `C:\xampp\htdocs\`.

### Étape 3 : Créer la base de données

1. Ouvre phpMyAdmin à l'adresse `http://localhost/phpmyadmin`.
2. Crée une base de données nommée `itop`.

### Étape 4 : Lancer l'installation

1. Ouvre `http://localhost/itop` dans le navigateur.
2. Suis l'assistant d'installation et renseigne les paramètres de connexion à la base :
   - Serveur de base de données : `localhost`
   - Identifiant : `root`
   - Base de données : `itop`
3. Vérifie que les extensions PHP `gd`, `soap` et `zip` sont activées. Sans elles, l'assistant ne peut pas continuer.

### Étape 5 : Finaliser l'installation

Une fois l'installation terminée, l'interface principale d'iTop s'affiche. La plateforme est prête à être configurée selon les besoins du projet.

### Dépannage

- **MySQL ne démarre pas (conflit de port 3306) :** un autre processus utilise déjà le port. Vérifie avec `netstat -ano | findstr 3306`, puis arrête le processus concerné ou change le port de MySQL dans la configuration de XAMPP.
- **Les extensions PHP ne sont pas activées :** ouvre `php.ini` depuis XAMPP et retire le `;` devant `extension=gd`, `extension=soap` et `extension=zip`, puis redémarre Apache.

Le détail complet de l'installation, avec les captures d'écran, se trouve dans le chapitre 4 du rapport.

## Compilation du rapport

Le rapport se compile avec LaTeX. Il faut installer une distribution (TeX Live ou MiKTeX), ou utiliser [Overleaf](https://www.overleaf.com).

Dans Overleaf :
1. Crée un projet et importe les fichiers du dépôt, dossier `images/` compris.
2. Définis `main.tex` comme fichier principal.
3. Compile avec **pdfLaTeX** (ou **LuaLaTeX** si tu utilises la version à un seul fichier).

En ligne de commande :

```bash
pdflatex main.tex
pdflatex main.tex
```

Deux passes sont nécessaires pour que la table des matières et les numéros de page soient corrects.

## Présentation HTML

Le dossier `presentation_itop/` contient une présentation d'iTop au format HTML. Ouvre `presentation_itop/index.html` dans un navigateur.

