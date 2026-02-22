# 🛡️ Projet : EntraID Identity & Security Lab
*Simulation d'une infrastructure d'entreprise hybride sur un tenant Microsoft 365 E5.*

## 📌 Objectifs du Projet
Démontrer la maîtrise de la gestion des identités, de l'automatisation des accès, de la sécurisation RBAC, de l'implémentation de stratégies Zero Trust (Conditional Access) et de la gestion de parc via Intune.

---

## 🚀 Phase 1 : Gouvernance des Identités & Automatisation
Mise en place d'une structure multi-régions avec automatisation via des règles dynamiques.

- **Automation** : Configuration de règles basées sur l'attribut `jobTitle` (OData).
- **Logique** : Attribution automatique des membres aux groupes de direction.

> **📸 Preuve Technique : Syntaxe de la règle dynamique**
> ![Règle de syntaxe dynamique](Screenshots/rule.jpeg)

---

## 🛡️ Phase 2 : Principe du Moindre Privilège (RBAC)
Délégation de droits granulaire et protection des hiérarchies.

- **Délégation** : Attribution du rôle `User Administrator` à un compte de test.
- **Protection** : Vérification de l'impossibilité pour un Admin User de modifier un Global Admin.

> **📸 Preuve Technique : Échec de la réinitialisation (Protection hiérarchique)**
> ![Erreur de privilèges RBAC](Screenshots/reset-password.jpeg)

---

## 🔍 Phase 3 : Troubleshooting MFA & SSPR
Analyse des politiques de sécurité "Mandatory MFA" et mise en place du Self-Service Password Reset.

- **Paradoxe MFA** : Identification de l'écart entre le portail Legacy (status: Disabled) et la réalité du Tenant (MFA Mandatory).
- **Audit** : Analyse du succès de l'authentification forte (OATH verification code).

> **📸 Preuve Technique : Analyse des facteurs d'authentification**
> ![Statut Legacy MFA](Screenshots/MFA-status.jpeg)
> ![Log de connexion détaillé](Screenshots/sign-in.jpeg)
> ![Décomposition des facteurs MFA](Screenshots/sign-in1.jpeg)

---

## 💰 Phase 4 : Gestion des Licences par Groupe (Scalability)
Industrialisation de l'attribution des ressources via le Microsoft 365 Admin Center.

- **Héritage** : Vérification que les utilisateurs reçoivent leurs licences via l'appartenance au groupe dynamique (Status: Inherited).

> **📸 Preuve Technique : Assignation et héritage**
> ![Assignation au groupe](Screenshots/licence-group.jpeg)
> ![Statut de licence hérité](Screenshots/inherited-licence.jpeg)

---

## 🌍 Phase 5 : Zero Trust - Geofencing & Accès Conditionnel
Mise en place d'un périmètre de sécurité géographique.

- **Action** : Blocage de tout accès hors France/Canada.
- **Validation** : Test d'échec de connexion via VPN (Code d'erreur 53003).

> **📸 Preuve Technique : Blocage géographique actif**
> ![Impact de la règle CA](Screenshots/CA-rule.jpeg)
> ![Message d'accès refusé](Screenshots/access-denied.jpeg)
> ![Log d'échec CA 53003](Screenshots/CA-logs.jpeg)

---

## 🔐 Phase 6 : Protection du Management (MFA Ciblé)
Superposition des politiques de sécurité pour les rôles à haut risque.

- **Stratégie** : Forcer le MFA spécifique pour le groupe `Management`.
- **Résultat** : Validation du succès de la politique personnalisée.

> **📸 Preuve Technique : Success log pour la politique Management**
> ![Règle MFA Management](Screenshots/mfa-management-rule.jpeg)
> ![Validation du succès MFA](Screenshots/mfa-management-log.jpeg)

---

## 🤖 Phase 7 : Identity Protection & Risky Sign-ins
Démonstration de la défense proactive face aux comportements suspects.

- **Smart Lockout** : Observation du verrouillage automatique du compte suite à des tentatives infructueuses via Tor.
- **CA Enforcement** : Blocage réussi une fois l'authentification réussie, prouvant que le contexte l'emporte sur l'identifiant.

> **📸 Preuve Technique : Détection et blocage de risque**
> ![Smart Lockout message](Screenshots/access-denied1.png)
> ![Analyse du log de risque 53003](Screenshots/logs2.jpeg)
> *Note : Le log confirme que malgré un mot de passe valide, l'accès est révoqué en raison du contexte de connexion non-conforme.*

---

## 💻 Phase 8 : Modern Endpoint Management (MDM Enrollment)
Jonction d'appareils Windows 11 dans un environnement Cloud Natif via Microsoft Intune.

- **Processus** : Configuration de l'OOBE (Out Of Box Experience) avec jointure Entra ID directe.
- **Sécurité** : Application stricte du MFA lors de l'enrôlement et limitation du nombre d'appareils par utilisateur.
- **Autorité MDM** : Configuration des scopes MDM/MAM pour garantir une gestion complète du parc.

> **📸 Preuve Technique : Enrôlement réussi avec MFA**
> ![MFA requis à l'enrôlement](Screenshots/Capture_d’écran_2026-02-22_080905.png)
> ![Bureau utilisateur managé](Screenshots/81212.png)

---

## 🛠️ Phase 9 : Automatisation des Droits Locaux
Solution d'ingénierie pour automatiser les privilèges administrateurs sans intervention du support.

- **Problématique** : Friction lors de l'onboarding d'utilisateurs nécessitant des droits admin locaux.
- **Solution** : Implémentation d'une politique `Local User Group Membership` via Intune Endpoint Security.
- **Résultat** : Injection automatique de l'utilisateur dans le groupe local `Administrators` dès la première connexion.
- **Sécurité** : Activation de **Microsoft Entra LAPS** pour sécuriser les comptes de secours locaux.

> **📸 Preuve Technique : Vérification de l'escalade de privilèges**
> ![Statut administrateur vérifié](Screenshots/Capture_d’écran_2026-02-22_082120.png)
> ![Détails du groupe local Administrators](Screenshots/Capture_d’écran_2026-02-22_081503.png)

---

## 🛡️ Phase 10 : Gouvernance de la Conformité (Compliance Policies)
Mise en place d'un "contrôle technique" automatique pour garantir l'hygiène du parc informatique.

- **Objectif** : Détecter et isoler les appareils dont la configuration de sécurité a été altérée.
- **Configuration** : Création d'une politique exigeant l'activation du Pare-feu et de l'Antivirus.
- **Résultat** : Détection de la non-conformité par Intune suite à la désactivation manuelle du firewall sur la VM.

> **📸 Preuve Technique : Cycle de vie de la conformité**
> ![Configuration de la politique Firewall](Screenshots/Screenshot_22-2-2026_8561_intune.microsoft.com.jpeg)
> ![Désactivation manuelle du pare-feu sur le client](Screenshots/085915.png)
> ![Appareil déclaré Non-compliant dans Intune](Screenshots/Screenshot_22-2-2026_972_intune.microsoft.com.jpeg)
> ![Détail de l'échec de la règle](Screenshots/Screenshot_22-2-2026_9634_intune.microsoft.com.jpeg)

---

## 🔒 Phase 11 : Enforcement Zero Trust (Accès Conditionnel + Compliance)
L'accès aux données est conditionné par la santé en temps réel de l'appareil.

- **Mécanisme** : Liaison entre Microsoft Intune (santé) et Entra ID (accès).
- **Logique** : Utilisation d'un filtre de device (`device.isCompliant -eq False`) pour cibler les terminaux à risque.
- **Résultat** : L'accès aux ressources est automatiquement révoqué si l'appareil est marqué non-conforme.

> **📸 Preuve Technique : Le bouclage Zero Trust**
> ![Filtre de non-conformité](Screenshots/Screenshot_22-2-2026_94241_entra.microsoft.com.jpeg)
> ![Politique de blocage active](Screenshots/Screenshot_22-2-2026_94214_entra.microsoft.com.jpeg)
> ![Message d'erreur d'accès refusé](Screenshots/094953.png)
Test de réversibilité validé : le rétablissement de la conformité sur le terminal lève instantanément les restrictions d'accès, prouvant la réactivité du moteur de sécurité Microsoft 365.
