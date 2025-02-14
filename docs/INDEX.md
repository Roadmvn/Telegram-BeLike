# Documentation Technique - Messagerie Sécurisée

## Spécifications Fonctionnelles
- [Authentification et Sécurité](core-features/auth-security.md)
  - Connexion anonyme
  - Chiffrement E2E
  - Gestion des clés
- [Gestion des Groupes](core-features/groups-management.md)
  - Création et administration
  - Limites et permissions
  - Invitations sécurisées
- [Gestion Multimédia](core-features/media-handling.md)
  - Stockage chiffré
  - Compression adaptative
  - Suppression programmée
- [Gestion des Utilisateurs](core-features/user-management.md)
  - Profils anonymes
  - Gestion des contacts
  - Synchronisation multi-devices
- [Contrôles de Confidentialité](core-features/privacy-controls.md)
  - Conformité GDPR
  - Suppression des données
  - Contrôles d'accès

## Spécifications Techniques
- [Architecture Frontend](technical-specs/frontend.md)
  - Stack React/Material-UI
  - État global et optimisation
  - Gestion offline
- [Architecture Backend](technical-specs/backend.md)
  - Services Spring Boot
  - WebSocket/MQTT
  - Scalabilité
- [Schéma de Base de Données](technical-specs/database.md)
  - Modèle de données
  - Indexes et performances
  - Chiffrement au repos

## Diagrammes
- [Flux d'Authentification](diagrams/auth-flow.puml)
- [Chiffrement des Messages](diagrams/message-e2ee.puml)
- [Architecture des Groupes](diagrams/group-arch.puml)