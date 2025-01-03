# 🚀 Installation GPO Sécurité 

## 🔒 1. Blocage accès au panneau de configuration

Accèder à l'interface de gestion des GPO : 

- Cliquer sur `Tools` puis `Group Policy Management`
- Dans le dossier Group Policy Objects clic droit puis New
- Nommer la GPO **"User-Security-ControlPanel-Deny"**
- Cette GPO s'appliquera sur les utilisateurs, dans l'onglet détail choisir  `GPO Statuts : Computer configuration settings disabled`
- Clic droit sur la GPO puis `Edit`
- User Configuration → Policies → Administrative Templates → Control Panel
- Double clic sur `Prohibit access to Control Panel and PC settings`
- Selectionner `Enabled` et OK

![enabled](https://github.com/WildCodeSchool/TSSR-2402-P3-G3-BuildYourInfra-Ekoloclast/blob/main/S11/captureGPO/enabled.PNG?raw=true)

- Lier cette GPO à l'OU LabUtilisateurs : clic droit puis "Link an Existing GPO"

**La GPO est bien liée à l'OU LabUtilisateurs.**

![link](https://github.com/WildCodeSchool/TSSR-2402-P3-G3-BuildYourInfra-Ekoloclast/blob/main/S11/captureGPO/link.PNG?raw=true)

---

## 🛡️ 2. Politique de mot de passe

- Cliquer sur `Tools` puis `Group Policy Management`
- Dans le dossier Group Policy Objects clic droit puis New
- Nommer la GPO "Computeur-Password-Policy"
- Cette GPO s'appliquera sur les ordinateurs, dans l'onglet détail choisir  `GPO Statuts : User configuration settings disabled`
- Clic droit sur la GPO puis `Edit`
- **Computeur Configuration → Policies → Windows Settings → Security Settings → Account Policy → Password Policy**

| Action | Paramètre | Statut |
| ------ | ------- | ------ |
| L'utilisateur doit définir 12 mots de passe différents pour pouvoir en réutiliser un | Enforce password history | Cocher : `Define this policy setting` → 12 |
| Le mdp doit être changé au bout de 60 jours | Maximum password age | Cocher : `Define this policy setting` → 60 |
| La durée minimale du mdp est de 30 jours | Minimum password age | Cocher : `Define this policy setting` → 30 |
| Le mdp doit contenir 8 charactères au minimum | Minimum password length | Cocher : `Define this policy setting` → 8 |
| Le mdp doit comprendre au moins une lettre majuscule, une lettre minuscule, un chiffre et un caractère spécial | Password must meet complexity requirements | Cocher : `Define this policy setting` → Enabled |
| Désactiver le stockage des mots de passe | Store passwords using reversible encryption | Disabled |

![password](https://github.com/WildCodeSchool/TSSR-2402-P3-G3-BuildYourInfra-Ekoloclast/blob/main/S11/captureGPO/password.PNG?raw=true)

- Lier cette GPO à l'OU LabOrdinateurs : clic droit puis "Link an Existing GPO"

---

## 🔐 3. Verrouillage de compte (suite à 5 mots de passe erronés)

- Cliquer sur `Tools` puis `Group Policy Management`
- Dans le dossier Group Policy Objects clic droit puis New
- Nommer la GPO "Computeur-Lock-Account"
- Cette GPO s'appliquera sur les ordinateurs, dans l'onglet détail choisir  `GPO Statuts : User configuration settings disabled`
- Clic droit sur la GPO puis `Edit`
- **Computeur Configuration → Policies → Windows Settings → Security Settings → Account Policy → Account Lockout Policy**

| Action | Paramètre | Statut |
| ------ | ------- | ------ |
| Après 5 tentatives de mdp, le compte sera vérouillé pendant 45 minutes | Account lockout duration | Cocher : `Define this policy setting` → 45 minutes |
| Le compte se vérouille après 5 tentatives incorrectes | Account lockout threshold | Cocher : `Define this policy setting` → 5 invalid logon |
| Le compteur du mot de passe erroné revient à 0 au bout de 15 minutes | Reset Lockout counter after | Cocher : `Define this policy setting` → 15 minutes |

- Lier cette GPO à l'OU LabOrdinateurs : clic droit puis "Link an Existing GPO"

---

## 🗂️ 4. Blocage accès à la base de registre

Accèder à l'interface de gestion des GPO : 

- Cliquer sur `Tools` puis `Group Policy Management`
- Dans le dossier Group Policy Objects clic droit puis New
- Nommer la GPO **"User-Registry-Deny"**
- Cette GPO s'appliquera sur les utilisateurs, dans l'onglet détail choisir  `GPO Statuts : Computer configuration settings disabled`
- Clic droit sur la GPO puis `Edit`
- User Configuration → Policies → Administrative Templates → System
- Double clic sur `Prevent access to registry editing tools`
- Selectionner `Enabled` et OK

- Lier cette GPO à l'OU LabUtilisateurs : clic droit puis "Link an Existing GPO"

---
