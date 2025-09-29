# Architecture Serverless 
Modèle de développement cloud-native qui permet de créer et d'exécuter des applications sans avoir à gérer des serveurs.

Les serveurs sont dissociés du développement d’applications

Architecture serverless désigne une approche de conception où les applications ne sont lancées que lorsqu'elles sont nécessaires

Il existe plusieurs catégories d'informatique serverless :

- **Function-as-a-Service (FaaS) :** Exécute des fonctions orientées événements dans des conteneurs éphémères. Il évite d'avoir à gérer les instances de serveur et s'exécute uniquement lorsqu'il est déclenché.
- **Backend-as-a-Service (BaaS)** : Offre des services back-end entièrement gérés qui couvrent l'authentification, les bases de données, la messagerie et le stockage. Ce modèle est souvent utilisé pour les applications web et mobiles.
- **Bases de données serverless** : Ces bases de données sont automatiquement mises à l'échelle et ne nécessitent aucune gestion de l'infrastructure.
- **Conteneurs serverless** : Ces conteneurs ne nécessitent aucun provisionnement manuel et se mettent à l'échelle de façon dynamique.
- **Edge computing serverless** : Le code s'exécute plus près des utilisateurs afin de réduire la latence.

### **Points forts**

- Pas de gestion d’infrastructure.
- Scalabilité automatique.
- Coûts optimisés à l’usage.
- Rapidité de mise en œuvre.

### **Limites**

- Latence possible au premier appel (*cold start*).
- Durée d’exécution limitée.
- Forte dépendance au fournisseur cloud.
- Moins de contrôle fin sur l’environnement.

Idéal pour les **microservices, APIs, traitements ponctuels et apps mobiles/web**, il combine **simplicité, flexibilité et scalabilité**

## Solutions NoCode

**`bubble.io`**

- Création d’app web (full stack no code).
- Points forts : flexible, permet de gérer la logique, la bdd, les workflows (app web complexes).
- Inconvénients : courbe d’apprentissage, Performance, dépendance de la plateforme.

**`Retool`** 

- Utilisé pour la création d’outils internes (dashboard, panneaux d’admin).
- Points forts : Excellant pour connecter des données réelles (API etc).
- Inconvénients : Nécessite des compétences techniques (JS, SQL).

**`webflow`**

- Utilisé pour la création de site web, pages marketing, site avec un design poussé.
- Point Forts : Excellant pour le design, animations, sites vitrnes (Génère du html / css).
- Inconvénients : Pas conçu pour la logique complexe ou interactions lourdes.

**`FlutterFlow`**

- Utilisé pour les applications mobiles ou web cross-platform.
- Points forts : Génère des apps mobiles et web basées sur le framework Flutter, avec interface visuelles + logique. Utile pour les apps qui ont un front + logique.
- Inconvénient : Limité pour des backend très complexes ou interactions lourdes.

**`Notion(product)`**

- Utilisé pour la gestion de produit, documentation, roadmap, backoffice léger.
- Points forts : Centralisation / organisation de la documentation (feedbacks utilisateurs).
- Inconvénients : Pas un outils de développement.