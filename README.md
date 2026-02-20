# 🛡️ Projet : EntraID Identity & Security Lab
*Simulation d'une infrastructure d'entreprise hybride sur un tenant Microsoft 365 E5.*

## 📌 Objectifs du Projet
Ce laboratoire démontre la maîtrise de la gestion des identités, de l'automatisation des accès et de la sécurisation des privilèges administratifs (RBAC) dans un environnement Cloud moderne.

---

## 🚀 Phase 1 : Gouvernance des Identités & Automatisation
Mise en place d'une structure de 10 utilisateurs multi-régions avec automatisation des accès via des règles dynamiques.

- **Groupes Dynamiques** : Configuration de règles basées sur les attributs (`JobTitle`).
- **Automatisation** : Utilisation de la syntaxe avancée pour capturer les profils de management.

> **📸 Preuve Technique : Syntaxe de la règle dynamique**
> ![Règle de syntaxe dynamique](screenshots/rule.jpeg)

---

## 🛡️ Phase 2 : Principe du Moindre Privilège (RBAC)
Délégation de droits granulaire et protection des comptes critiques.

- **Délégation** : Attribution du rôle `User Administrator` au compte Marc Lefebvre.
- **Test de Protection** : Vérification de l'impossibilité pour un Admin User de modifier un Global Admin.

> **📸 Preuve Technique : Échec de la réinitialisation (Protection hiérarchique)**
> ![Erreur de privilèges RBAC](screenshots/reset-password.jpeg)

---

## 🔍 Phase 3 : Troubleshooting & Sécurité (MFA & Logs)
Analyse des politiques de sécurité "Mandatory MFA" de Microsoft et diagnostic via les logs d'audit.

- **Le Paradoxe MFA** : Identification d'un statut "Disabled" sur le portail Legacy alors que la sécurité est appliquée au niveau du Tenant.

> **📸 Preuve Technique : Statut Legacy MFA (Affichage Trompeur)**
> ![Statut Legacy MFA](screenshots/MFA-status.jpeg)

- **Analyse des Logs** : Validation du succès de l'authentification forte (Authenticator) et décomposition des facteurs.

> **📸 Preuve Technique : Analyse du flux d'authentification (MFA Validé)**
> ![Log de connexion résumé](screenshots/sign-in.jpeg)
> ![Log de connexion détaillé](screenshots/sign-in1.jpeg)
> *On confirme ici la validation successive du mot de passe et du second facteur (code OATH).*

---

## 💰 Phase 4 : Gestion des Licences par Groupe (Scalability)
Industrialisation de l'attribution des ressources via le Microsoft 365 Admin Center.

- **Stratégie** : Attribution des licences Microsoft 365 E5 directement au groupe `Lyon`.
- **Héritage** : Vérification que les utilisateurs reçoivent leurs droits via l'appartenance au groupe.

> **📸 Preuve Technique : Assignation au groupe et statut hérité**
> ![Assignation au groupe](screenshots/licence-group.jpeg)
> ![Statut de licence hérité](screenshots/inherited-licence.jpeg)
> *L'utilisateur reçoit ses licences automatiquement via l'appartenance au groupe.*
