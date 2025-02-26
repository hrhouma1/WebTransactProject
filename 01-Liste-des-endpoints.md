Liste des endpoints extraits de **Mind Application** :

### **Plan Controller**
- **PUT** `/api/v1/plan/update/{id}` – Met à jour un plan spécifique.
- **PUT** `/api/v1/plan/delete/{id}` – Supprime un plan spécifique.
- **POST** `/api/v1/plan/add` – Ajoute un nouveau plan.

### **User Controller (Authentification & Gestion des Comptes)**
- **PUT** `/api/v1/auth/validateAccount/{verificationCode}` – Valide un compte utilisateur avec un code de vérification.
- **PUT** `/api/v1/auth/updateAccount` – Met à jour les informations du compte utilisateur.
- **PUT** `/api/v1/auth/resetPassword/{token}` – Réinitialise le mot de passe avec un token.
- **PUT** `/api/v1/auth/deleteUser` – Supprime un compte utilisateur.
- **POST** `/api/v1/auth/user/register` – Inscription d’un utilisateur.
- **POST** `/api/v1/auth/user/registerBySubscription` – Inscription d’un utilisateur via un abonnement.
- **POST** `/api/v1/auth/token` – Génère un token d'authentification.
- **POST** `/api/v1/auth/loginGoogle` – Connexion via Google.
- **POST** `/api/v1/auth/forgotPassword` – Demande de réinitialisation de mot de passe.
- **POST** `/api/v1/auth/admin/register` – Inscription d’un administrateur.
- **POST** `/api/v1/auth/addUserByAdmin` – Ajout d’un utilisateur par un administrateur.
- **GET** `/api/v1/auth/userinsesson` – Récupère les informations de l’utilisateur en session.

### **Payment Controller**
- **POST** `/api/v1/payment/create` – Crée un paiement.
- **POST** `/api/v1/payment/confirm` – Confirme un paiement.

