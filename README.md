# SGI_ITIRC
Un système d'information complet développé pour la gestion administrative, financière et logistique du Club ITIRC (ENSAO). Ce projet a été conçu dans le cadre du module académique de Python/SQL, en alliant modélisation de base de données avancée et développement d'une API backend robuste.

🎯 Objectif du Projet
Ce projet vise à numériser et centraliser l'organisation du club à travers son architecture en cellules. Il permet au Pilotage et au Bureau de gérer les membres (3A, 4A, 5A), de suivre les cotisations mensuelles, et d'organiser efficacement les événements (comme la Journée de Filière) en assignant des tâches spécifiques à chaque cellule (Média, Formation, Rédaction, etc.).

✨ Fonctionnalités Principales
Gestion des Ressources Humaines : Suivi des membres, de leurs rôles hiérarchiques (Pilotage, Bureau, Membres) et de leur affectation aux différentes cellules spécialisées.

Suivi de Trésorerie : Enregistrement des cotisations mensuelles avec détection automatique des retards de paiement via des vues SQL.

Gestion Événementielle : Création d'événements, allocation de budget et assignation de tâches de préparation aux membres selon leurs cellules.

Audit et Sécurité : Traçabilité des actions sensibles (ex: modifications financières) assurée de manière autonome par le moteur de base de données.

🛠️ Architecture Technique
Le projet repose sur une séparation stricte entre la couche de données et l'API :

Base de Données (SQL) : Modélisation relationnelle complète exploitant des concepts avancés pour garantir l'intégrité et la logique métier exigées :

Vues (VIEW) : Génération de tableaux de bord instantanés (ex: état global de la trésorerie).

Déclencheurs (TRIGGER) : Système d'audit (historique des modifications) et restrictions métier (ex: blocage d'assignation à un événement si la cotisation est impayée).

Procédures Stockées (PROCEDURE) : Automatisation des processus transactionnels complexes (ex: clôture définitive d'un événement et libération des ressources).

Back-end (Python / FastAPI) : API RESTful documentée automatiquement (Swagger) permettant de lier l'interface utilisateur au moteur de base de données.
