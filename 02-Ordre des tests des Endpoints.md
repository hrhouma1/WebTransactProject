# **Ordre des tests des Endpoints**

### **1️⃣ Authentification et Gestion des Comptes (Tester en premier)**
💡 *Objectif : S'assurer que l'authentification et la gestion des utilisateurs fonctionnent avant d'aller plus loin.*

1. **Inscription et Authentification**
   - ✅ **POST** `/api/v1/auth/user/register` – Inscrire un nouvel utilisateur.
   - ✅ **POST** `/api/v1/auth/user/registerBySubscription` – Inscription via un abonnement.
   - ✅ **POST** `/api/v1/auth/loginGoogle` – Connexion via Google.
   - ✅ **POST** `/api/v1/auth/token` – Récupérer un token d’authentification.

2. **Validation et Gestion du Compte**
   - ✅ **PUT** `/api/v1/auth/validateAccount/{verificationCode}` – Valider le compte avec un code de vérification.
   - ✅ **GET** `/api/v1/auth/userinsesson` – Vérifier l’utilisateur en session.
   - ✅ **PUT** `/api/v1/auth/updateAccount` – Mettre à jour les informations du compte.
   - ✅ **POST** `/api/v1/auth/forgotPassword` – Demander une réinitialisation de mot de passe.
   - ✅ **PUT** `/api/v1/auth/resetPassword/{token}` – Réinitialiser le mot de passe avec un token.
   - ✅ **PUT** `/api/v1/auth/deleteUser` – Supprimer un compte utilisateur.

3. **Gestion par un Administrateur**
   - ✅ **POST** `/api/v1/auth/admin/register` – Inscription d’un administrateur.
   - ✅ **POST** `/api/v1/auth/addUserByAdmin` – Ajout d’un utilisateur par un administrateur.

---

### **2️⃣ Gestion des Plans (Tester après l’authentification)**
💡 *Objectif : Une fois connecté, l’utilisateur peut gérer ses plans.*

4. **Créer et Gérer un Plan**
   - ✅ **POST** `/api/v1/plan/add` – Ajouter un nouveau plan.
   - ✅ **PUT** `/api/v1/plan/update/{id}` – Mettre à jour un plan existant.
   - ✅ **PUT** `/api/v1/plan/delete/{id}` – Supprimer un plan.

---

### **3️⃣ Gestion des Paiements (Tester en dernier)**
💡 *Objectif : Une fois les plans prêts, tester les paiements.*

5. **Effectuer un Paiement**
   - ✅ **POST** `/api/v1/payment/create` – Créer un paiement.
   - ✅ **POST** `/api/v1/payment/confirm` – Confirmer un paiement.

---

## **Explication de la stratégie**
1. **Tester l’authentification** en premier (sinon impossible d’accéder aux autres fonctionnalités sécurisées).
2. **Gérer les comptes et les utilisateurs** (modification du profil, récupération de mot de passe).
3. **Tester la gestion des plans** (ajout, modification, suppression).
4. **Enfin, tester les paiements** (car cela dépend des comptes et des plans).


Voici l’ordre recommandé pour tester les endpoints sur **Swagger** avant de développer l’interface web. L'objectif est de suivre une logique cohérente : **authentification**, **gestion des comptes**, **gestion des plans**, et enfin **paiements**.
Avec cette méthodologie, tes étudiants pourront tester les endpoints dans un ordre logique et progresser étape par étape. **Si tu veux, je peux aussi rédiger l’énoncé de l’exercice pour toi !** 🚀
---
