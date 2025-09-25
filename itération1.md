# Concepts architecture logicielle

## Architecture logicielle
Structure d’un système logiciel définissant ses **composants**, leurs **interactions** et leurs **contraintes**.

**Objectif :** garantir **qualité**, **maintenabilité**, **scalabilité** et **performance**.

---

## Exécution d’un logiciel
1. **Écriture du code source** (par un développeur).  
2. **Compilation ou interprétation** (selon le langage).  
3. **Exécution** sur une machine.

---

## Styles de programmation
Manière d’organiser le code dans un projet.

- **Monolithique** → tout en un bloc.  
- **Client-serveur** → séparation entre client et serveur.

---

## Paradigmes de programmation
Manière de programmer basée sur un ensemble de principes.

- **Programmation impérative** : suite d’instructions exécutées dans l'ordre où elles sont écrites.  
- **Programmation fonctionnelle** : les données ne sont modifiées que par des fonctions, qui prennent des paramètres et renvoient des données de sortie.  
- **Programmation orientée objet** : le programme est vu comme l’interaction d’objets ayant des attributs (caractéristiques) et des méthodes (actions).  
- **Programmation événementielle** : le programme réagit aux événements (ex. JavaScript).

---

## Langages de programmation
Outils permettant d’écrire des programmes.

- **Bas niveau** : Assembleur, C.  
- **Haut niveau** : Java, Python, PHP.  
- **Spécialisés** : SQL (bases de données), R (statistiques).

**Choix du langage influencé par :**
- Performance.  
- Portabilité.  
- Écosystème (librairies, frameworks).

---

## Persistance des données
Capacité à **conserver les données au-delà de l’exécution** d’un programme.

- **Bases de données relationnelles** (SQL : MySQL, PostgreSQL).  
- **Bases de données NoSQL** (MongoDB).  
- **Sérialisation** (sauvegarde d’objets dans un format lisible).

---

## Modélisation
Représentation abstraite d’un système pour mieux le concevoir.

**Objectif :** simplifier la compréhension et faciliter la communication entre parties prenantes.

---

## Patrons de conception (*Design Patterns*)
Solutions génériques à des problèmes récurrents de conception logicielle.

**Avantages :** réutilisabilité, maintenabilité, lisibilité.

**Trois familles de patrons :**
- **Créationnels** : définissent comment instancier et configurer classes et objets.  
- **Structurels** : organisent les classes dans une structure plus large, séparant interface et implémentation.  
- **Comportementaux** : organisent la collaboration entre objets et définissent les algorithmes impliqués.

---

## Architecture en couches
Représentée comme une maison avec des étages séparés :  

- **Couche Présentation (UI)** : visible par l’utilisateur.  
- **Couche Logique métier** : règles du jeu, logique interne.  
- **Couche Données** : stockage des joueurs, parties, résultats.  

Chaque couche est indépendante : une modification dans le design n’impacte pas la logique métier et inversement.