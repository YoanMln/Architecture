# Architectures distribuées

## Communication Client / Serveur

Modèle architectural fondamental qui définit la façon dont les applications et systèmes échangent des informations sur un réseau. 

### Principe de base

- **Serveur** : Programme ou machine qui fournit des services, ressources ou données (serveur web, serveur de BDD, etc.)
- **Client** : Programme qui demande des services au serveur. Initialise la communication en envoyant des requêtes. 

### Fonctionnement

1. **Connexion** : le client établit une connexion avec le serveur (souvent via TCP/IP)  
2. **Requête** : le client envoie une demande spécifique au serveur  
3. **Traitement** : le serveur analyse la requête et prépare la réponse  
4. **Réponse** : le serveur renvoie les données ou confirme l'action  
5. **Déconnexion** : la communication se termine (ou reste ouverte selon le protocole)  

### Avantages

- **Centralisation** : les données et la logique métier sont centralisées sur le serveur  
- **Sécurité** : contrôle d'accès centralisé et sécurisation des données sensibles  
- **Scalabilité** : possibilité d'ajouter plus de serveurs pour gérer la charge  

### Inconvénients

- **Point de défaillance** : si le serveur tombe, tous les clients sont impactés  
- **Dépendance réseau** : nécessite une connexion stable  
- **Latence** : délais dus aux communications réseau  

---

## Client léger / Client lourd

### Client léger

Application qui délègue la majorité du traitement et de la logique métier au serveur.  

**Caractéristiques :**  
- Interface utilisateur minimale  
- Faible consommation de ressources locales  
- Forte dépendance au serveur  

**Exemples :**  
- Applications web (Gmail, Google Docs) : tout se passe dans le navigateur  
- Terminaux bancaires : simples interfaces pour saisir les données  

---

### Client lourd

Application qui effectue une grande partie du traitement en local. Possède sa propre logique métier et peut fonctionner partiellement hors ligne.  

**Caractéristiques :**  
- Logique métier intégrée dans le client  
- Consommation importante de ressources locales  
- Installation et maintenance sur chaque poste  

**Exemples :**  
- Logiciels de bureautique : Microsoft Office, Photoshop  
- Jeux vidéo : la plupart des jeux PC/console  



### Comparaison

                                                                                
| Aspect                    | Client léger        | Client lourd                 |
|---------------------------|---------------------|------------------------------|
| **Installation**          | Navigateur suffit   | Installation complète        |
| **Maintenance**           | Centralisée         | Sur chaque poste             |
| **Performance**           | Dépend du réseau    | Performance locale           |
| **Fonctionnement hors ligne** | Limité/impossible | Souvent possible           |
| **Sécurité**              | Centralisée serveur | Distribuée                   |
| **Coût déploiement**      | Faible              | Élevé                        |
|                                                                                |


## Serveurs

### Serveur Web

**Fonctions principales :**  
- Recevoir les requêtes HTTP/HTTPS des clients (navigateurs)  
- Servir des pages web, images, fichiers CSS/JS  
- Gérer les protocoles de communication web  

**Technologies courantes :**  
- **Apache** : le plus répandu, très configurable  
- **Nginx** : performant pour la charge et les fichiers statiques  

**Exemples :**  
- Hébergement de sites vitrines  

---

### Serveur de Base de Données

Stocke, organise et gère l'accès aux données de manière structurée et sécurisée.  

**Fonctions principales :**  
- Stocker les données de façon organisée  
- Optimiser les performances de recherche  

**Technologies courantes :**  
- MySQL : web et applications légères  
- Oracle Database : entreprises et gros volumes  

**Exemples concrets :**  
- Stocker les comptes utilisateurs d’un site web  
- Gérer l’inventaire d’un magasin en ligne  

---

### Serveur d’Application

Exécute la logique métier et fait le lien entre l’interface utilisateur et les données.  

**Fonctions principales :**  
- Exécuter le code de l’application (logique métier)  
- Gérer les authentifications  
- Gérer les transactions et la sécurité  

**Technologies courantes :**  
- Node.js : JavaScript côté serveur  
- Apache Tomcat : applications Java  
- PHP-FPM : traitement PHP  

**Exemples concrets :**  
- Calculer le prix d’un panier e-commerce  
- Valider un formulaire d’inscription et créer un compte  

---

## Schémas architectures

# Architectures Logicielles

## Architecture Monolithe (Simple)

```
                 ┌───────────────────────────┐
                 │        CLIENTS            │
                 │                           │
                 │ • Navigateur Web          │
                 │ • Application mobile      │
                 │ • Client lourd (ex: ERP)  │
                 └─────────────▲─────────────┘
                               │ Requêtes (HTTP, API, etc.)
                               ▼
 ┌─────────────────────────────────────────────────────────┐
 │                       SERVEUR WEB                       │
 │  - Reçoit les requêtes des clients                      │
 │  - Sert les pages web / APIs                            │
 └─────────────▲──────────────────────────────────────────-┘
               │
               ▼
 ┌─────────────────────────────────────────────────────────┐
 │                 SERVEUR D'APPLICATION                   │
 │  - Contient la logique métier (authentification,        │
 │    gestion commandes, calculs, etc.)                    │
 └─────────────▲──────────────────────────────────────────-┘
               │
               ▼
 ┌───────────────────────────┐     ┌───────────────────────────┐
 │   SERVEUR BASE DE DONNÉES │     │    SERVEUR DE TEMPS (NTP) │
 │  - Stocke utilisateurs    │     │  - Synchronisation horaire│
 │  - Inventaire, commandes  │     └───────────────────────────┘
 │  - Transactions           │
 └───────────────────────────┘
```

### Caractéristiques
- Une seule application déployée d'un bloc
- BDD unique partagée

### Avantages
- Simple à développer et tester
- Déploiement simple

### Inconvénients
- Déploiement complexe des mises à jour
- Technologie unique

---

## Architecture 3 Tiers (Séparation des rôles)

```
┌─────────────────────────────────────────┐
│              NIVEAU 1                   │
│          PRÉSENTATION                   │
│                                         │
│  ┌─────────────┐  ┌─────────────┐       │
│  │   Client    │  │  Serveur    │       │
│  │    Web      │  │    Web      │       │
│  │ (Navigateur)│  │  (Apache,   │       │
│  │             │  │   Nginx)    │       │
│  └─────────────┘  └─────────────┘       │
└─────────────────────────────────────────┘
                    │
                    ▼
┌─────────────────────────────────────────┐
│              NIVEAU 2                   │
│          LOGIQUE MÉTIER                 │
│                                         │
│  ┌─────────────────────────────────────┐│
│  │      Serveur d'Application          ││
│  │                                     ││
│  │  • Authentification                 ││
│  │  • Rules Business                   ││
│  │  • Traitements                      ││
│  │  • API / Services                   ││
│  └─────────────────────────────────────┘│
└─────────────────────────────────────────┘
                    │
                    ▼
┌─────────────────────────────────────────┐
│              NIVEAU 3                   │
│             DONNÉES                     │
│                                         │
│  ┌─────────────────────────────────────┐│
│  │      Serveur de Base de Données     ││
│  │                                     ││
│  │  • Stockage                         ││
│  │  • Requêtes SQL                     ││
│  │  • Intégrité                        ││
│  └─────────────────────────────────────┘│
└─────────────────────────────────────────┘
```

### Caractéristiques
- Séparation claire des rôles
- Maintenance facilitée par couche

### Inconvénients
- Latences réseau entre les couches
- Plus complexe que le monolithe

---

## N Tiers / Multi-couches

```
┌─────────────────────────────────────────┐
│           NIVEAU PRÉSENTATION           │
│  ┌─────────┐ ┌─────────┐ ┌─────────┐    │
│  │   Web   │ │ Mobile  │ │Desktop  │    │
│  │ Client  │ │   App   │ │   App   │    │
│  └─────────┘ └─────────┘ └─────────┘    │
└─────────────────────────────────────────┘
                    │
                    ▼
┌─────────────────────────────────────────┐
│             NIVEAU WEB                  │
│  ┌─────────────────────────────────────┐│
│  │      Serveurs Web (Load Balancer)   ││
│  └─────────────────────────────────────┘│
└─────────────────────────────────────────┘
                    │
                    ▼
┌─────────────────────────────────────────┐
│           NIVEAU SERVICES               │
│  ┌─────────┐ ┌─────────┐ ┌─────────┐    │
│  │Service  │ │Service  │ │Service  │    │
│  │Authent. │ │Commande │ │Payment  │    │
│  └─────────┘ └─────────┘ └─────────┘    │
└─────────────────────────────────────────┘
                    │
                    ▼
┌─────────────────────────────────────────┐
│          NIVEAU LOGIQUE MÉTIER          │
│  ┌─────────────────────────────────────┐│
│  │       Serveurs d'Application        ││
│  │  • Rules Engine                     ││
│  │  • Workflow Management              ││
│  │  • Business Logic                   ││
│  └─────────────────────────────────────┘│
└─────────────────────────────────────────┘
                    │
                    ▼
┌─────────────────────────────────────────┐
│           NIVEAU INTÉGRATION            │
│  ┌─────────┐ ┌─────────┐ ┌─────────┐    │
│  │   ERP   │ │   CRM   │ │External │    │
│  │Connect. │ │Connect. │ │   API   │    │
│  └─────────┘ └─────────┘ └─────────┘    │
└─────────────────────────────────────────┘
                    │
                    ▼
┌─────────────────────────────────────────┐
│            NIVEAU DONNÉES               │
│  ┌─────────┐ ┌─────────┐ ┌─────────┐    │
│  │   DB    │ │  Data   │ │  Cache  │    │
│  │Principal│ │Warehouse│ │ (Redis) │    │
│  └─────────┘ └─────────┘ └─────────┘    │
└─────────────────────────────────────────┘
```

### Caractéristiques
- Multiplication des couches selon les besoins
- Flexibilité architecturale

### Avantages
- Technologies spécialisées par niveau
- Maintenance ciblée par couche

### Inconvénients
- Latence cumulée entre couches
- Complexité de gestion élevée

---

## Microservices (Autonomie complète)

```
┌─────────────────────────────────────────┐
│              CLIENTS                    │
│  ┌─────────┐ ┌─────────┐ ┌─────────┐    │
│  │   Web   │ │ Mobile  │ │Partners │    │
│  │  Apps   │ │  Apps   │ │   API   │    │
│  └─────────┘ └─────────┘ └─────────┘    │
└─────────────────────────────────────────┘
                    │
                    ▼
┌─────────────────────────────────────────┐
│            API GATEWAY                  │
│         (Routage, Authentification,     │
│          Load Balancing, Monitoring)    │
└─────────────────────────────────────────┘
                    │
        ┌───────────┼───────────┐
        │           │           │
        ▼           ▼           ▼
┌─────────────┐ ┌─────────────┐ ┌─────────────┐
│   SERVICE   │ │   SERVICE   │ │   SERVICE   │
│ UTILISATEUR │ │  COMMANDE   │ │  PRODUIT    │
│             │ │             │ │             │
│ ┌─────────┐ │ │ ┌─────────┐ │ │ ┌─────────┐ │
│ │   API   │ │ │ │   API   │ │ │ │   API   │ │
│ └─────────┘ │ │ └─────────┘ │ │ └─────────┘ │
│ ┌─────────┐ │ │ ┌─────────┐ │ │ ┌─────────┐ │
│ │Business │ │ │ │Business │ │ │ │Business │ │
│ │  Logic  │ │ │ │  Logic  │ │ │ │  Logic  │ │
│ └─────────┘ │ │ └─────────┘ │ │ └─────────┘ │
│ ┌─────────┐ │ │ ┌─────────┐ │ │ ┌─────────┐ │
│ │   DB    │ │ │ │   DB    │ │ │ │   DB    │ │
│ │  Users  │ │ │ │ Orders  │ │ │ │Products │ │
│ └─────────┘ │ │ └─────────┘ │ │ └─────────┘ │
└─────────────┘ └─────────────┘ └─────────────┘

        ┌───────────┼───────────┐
        ▼           ▼           ▼
┌─────────────┐ ┌─────────────┐ ┌─────────────┐
│   SERVICE   │ │   SERVICE   │ │   SERVICE   │
│  PAIEMENT   │ │NOTIFICATION │ │  REPORTING  │
│             │ │             │ │             │
│ ┌─────────┐ │ │ ┌─────────┐ │ │ ┌─────────┐ │
│ │   API   │ │ │ │   API   │ │ │ │   API   │ │
│ └─────────┘ │ │ └─────────┘ │ │ └─────────┘ │
│ ┌─────────┐ │ │ ┌─────────┐ │ │ ┌─────────┐ │
│ │Business │ │ │ │Business │ │ │ │Business │ │
│ │  Logic  │ │ │ │  Logic  │ │ │ │  Logic  │ │
│ └─────────┘ │ │ └─────────┘ │ │ └─────────┘ │
│ ┌─────────┐ │ │ ┌─────────┐ │ │ ┌─────────┐ │
│ │   DB    │ │ │ │Message  │ │ │ │Analytics│ │
│ │Payments │ │ │ │ Queue   │ │ │ │   DB    │ │
│ └─────────┘ │ │ └─────────┘ │ │ └─────────┘ │
└─────────────┘ └─────────────┘ └─────────────┘
```

### Caractéristiques
- Services indépendants et autonomes
- Communication via API
- Technologies variées selon les besoins

### Avantages
- Panne isolée
- Déploiement continu facilité

### Inconvénients
- Complexité opérationnelle élevée
- Latence réseau entre services

