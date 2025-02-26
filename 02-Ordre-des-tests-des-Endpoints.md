# **Ordre des tests des Endpoints**


(MOHSEN0) ajouter la version actuelle au github et ajouter un tag - fin du Spring 1

### **1️⃣ Authentification et Gestion des Comptes (Tester en premier)**
💡 *Objectif : S'assurer que l'authentification et la gestion des utilisateurs fonctionnent avant d'aller plus loin.*


- Vous devez tester avec swaggerdans un premier temps.
- Vous devez developper des interfaces (3 interfaces : Register , Login et confirmation, Landing page de notre projet)
- Nous allons creer un utilisateur admin qui a acces a une 4eme interafce (la page administrative pour les plans uniquement pour l'admin)

1. **Inscription et Authentification pour un utilisateur normal**
   - ✅ **POST(REGISTER)** `/api/v1/auth/user/register` – Inscrire un nouvel utilisateur normal.
   - ✅ **PUT(VERFICATION-EMAIL)** `/api/v1/auth/validateAccount/{verificationCode}` – Valider le compte avec un code de vérification.
   - ✅ **POST(LOGIN)** `/api/v1/auth/token` – Récupérer un token d’authentification.


2. **Inscription et Authentification pour un utilisateur admin**
   - ✅ **POST** `/api/v1/auth/admin/register` – Inscription d’un administrateur.
   - Allez a la base de donnee et changer lattribut is_validated to true (dans la table user).
   - ✅ **POST(LOGIN)** `/api/v1/auth/token` – Récupérer un token d’authentification.



#### Optionnel (pour utilisateur admin, faire le put et je recevrai un email de validation)"
(MOSEN1) Ajouter le courriel du superadmin haythemrehouma@gmail.com (pour valider les admins)
   - ✅ **PUT(VERFICATION-EMAIL)** `/api/v1/auth/validateAccount/{verificationCode}` – Valider le compte avec un code de vérification.


### **2️⃣ Implementer le logout**

- Pas besoin d'API. il faut supprimer le token du localstorage. Dans ce cas, il faut utiliser le navigateur pour faire les verifications que le token a ete supprime.
- Vous devez developper cette interafce et le bouton pour supprimer le token du localstorage.


### **3️⃣ Il faut se loguer comme administrateur (regardez ci-haut)**

### **4  Gestion des Plans (Tester après l’authentification)**
💡 *Objectif : Une fois connecté, l’utilisateur peut gérer ses plans.*

2. **Créer et Gérer un Plan**
   - ✅ **POST** `/api/v1/plan/add` – Ajouter un nouveau plan.
   - ✅ **PUT** `/api/v1/plan/update/{id}` – Mettre à jour un plan existant.
   - ✅ **PUT** `/api/v1/plan/delete/{id}` – Supprimer un plan.

(MOSEN2) IMPLEMENTER LE GET
- Vous devez tester avec swagger dans un premier temps.
- Il s'agit de la partie administrative (utilisateur admin).
- Vous devez developper la page administrative pour les plans (1 seule interface).



### **2️5 Utiliser le logout**


### **2️ 6 (LANDING PAGE + TARIF)

Le client va a notre landing page (il nest pas connecte) . Il doit consulter les tarifs et choisir un plan et cliquer sur le bouton payer.


### **7 Gestion des Paiements (Tester en dernier)**
💡 *Objectif : Une fois les plans prêts, tester les paiements.*

7. **Effectuer un Paiement**
   - ✅ **POST** `/api/v1/payment/create` – Créer un paiement.
   - ✅ **POST** `/api/v1/payment/confirm` – Confirmer un paiement.

Remarque: Il ya les parametres a verifieer
il y a la reference du plan choisi qui va etre envoye  au backend (APi)


### **8 Gestion des Paiements - partie 2** (CAS la premiere fois, il nest jamais inscrit)
   - ✅ **POST** `/api/v1/auth/user/registerBySubscription` – Inscription via un abonnement.

- ceci va nous ramener vers la page register 
- page register a un token de subscribtion + 

(MOSEHN3) LE CAS OU iL EST DEJA LOGUE et qui a deja une susbscription quil veut renouveler
PENSER AU REFUND


### **9 Autres fonctionnalites


 **Validation et Gestion du Compte**
   
   - ✅ **GET** `/api/v1/auth/userinsesson` – Vérifier l’utilisateur en session (ADMIN  + USER NORMAL cote swagger, pas dinterface pour le debogauge)
   - ✅ **PUT** `/api/v1/auth/updateAccount` – Mettre à jour les informations du compte (ADMIN  + USER NORMAL + interafce)
   - ✅ **POST** `/api/v1/auth/forgotPassword` – Demander une réinitialisation de mot de passe (SANS LOGIN + interafce)
   - ✅ **PUT** `/api/v1/auth/resetPassword/{token}` – Réinitialiser le mot de passe avec un token (SANS LOGIN + interface)
   - ✅ **PUT** `/api/v1/auth/deleteUser` – Supprimer un compte utilisateur. (UNIQUEMENT ADMIN)

3. **Gestion par un Administrateur**
   - ✅ **POST** `/api/v1/auth/addUserByAdmin` – Ajout d’un utilisateur par un administrateur(ADMIN  + interface dans le back)


- Dernier defi pour avoir un 100%

  - ✅ **POST** `/api/v1/auth/loginGoogle` – Connexion via Google.






---

## **Explication de la stratégie**
1. **Tester l’authentification** en premier (sinon impossible d’accéder aux autres fonctionnalités sécurisées).
2. **Gérer les comptes et les utilisateurs** (modification du profil, récupération de mot de passe).
3. **Tester la gestion des plans** (ajout, modification, suppression).
4. **Enfin, tester les paiements** (car cela dépend des comptes et des plans).





















Voici l’ordre recommandé pour tester les endpoints sur **Swagger** avant de développer l’interface web. L'objectif est de suivre une logique cohérente : **authentification**, **gestion des comptes**, **gestion des plans**, et enfin **paiements**.
Avec cette méthodologie, tes étudiants pourront tester les endpoints dans un ordre logique et progresser étape par étape. **Si tu veux, je peux aussi rédiger l’énoncé de l’exercice pour toi !** 🚀
---
