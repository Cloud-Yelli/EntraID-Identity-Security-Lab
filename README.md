# 🛡️ Projet : EntraID Identity & Security Lab
*Simulation d'une infrastructure d'entreprise hybride (France/Canada) sur un tenant Microsoft 365 E5.*

## 📌 Objectifs du Projet
Ce laboratoire vise à démontrer la maîtrise de la gestion des identités, de l'automatisation des accès et de la sécurisation des privilèges administratifs (RBAC) dans un environnement Cloud moderne.

---

## 🚀 Phase 1 : Gouvernance des Identités & Automatisation
Mise en place d'une structure de 10 utilisateurs multi-régions avec automatisation des accès.

- **Groupes Dynamiques** : Configuration de règles basées sur les attributs (`City`, `JobTitle`).
  - *Exemple de syntaxe utilisée* : `(user.jobTitle -contains "Manager") -or (user.jobTitle -contains "Director")`
- **Automatisation** : Suppression du provisionnement manuel pour les localisations géographiques.

## 🛡️ Phase 2 : Principe du Moindre Privilège (RBAC)
Délégation de droits sans compromettre la sécurité globale du tenant.

- **Délégation** : Attribution du rôle `User Administrator` à un compte technicien (Marc Lefebvre).
- **Test de Protection** : Vérification de la hiérarchie Entra ID (Impossibilité pour un Admin User de modifier/supprimer un Global Admin).

## 🔍 Phase 3 : Troubleshooting & Sécurité (The "MFA" Case)
Analyse critique des nouvelles politiques de sécurité Microsoft 2025.

- **Diagnostic** : Identification du blocage MFA via les `Sign-in Logs`.
- **Analyse** : Étude du conflit entre le SSPR (Self-Service Password Reset) et les politiques de "Mandatory MFA" imposées par Microsoft pour les portails d'administration.
- **Résolution** : Configuration et validation des méthodes d'authentification forcées pour les rôles privilégiés.
