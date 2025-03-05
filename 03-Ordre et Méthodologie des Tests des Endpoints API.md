---
# **Ordre et Méthodologie des Tests des Endpoints API**
---

# 1 - Liste des endpoints

```ssh
+-------+---------+------------------------------------------------+------------------------------------------+
| Ordre | Méthode |                  Endpoint                     |               Description                |
+-------+---------+------------------------------------------------+------------------------------------------+
|   1   |  POST   | /api/v1/auth/user/register                     | Inscription utilisateur                  |
|   2   |   PUT   | /api/v1/auth/validateAccount/{verificationCode} | Validation de l'email                    |
|   3   |  POST   | /api/v1/auth/token                              | Connexion utilisateur                    |
|   4   |  POST   | /api/v1/auth/admin/register                     | Inscription administrateur               |
|   5   |   PUT   | /api/v1/auth/validateAccount/{verificationCode} | Validation administrateur                |
|   6   |  POST   | /api/v1/auth/token                              | Connexion administrateur                 |
|   7   | DELETE  | /api/v1/auth/deleteUser                         | Suppression d'un compte                  |
|   8   |   GET   | /api/v1/auth/userinsesson                       | Vérification de l'utilisateur en session |
|   9   |  POST   | /api/v1/auth/updateAccount                      | Mise à jour du compte                    |
|  10   |  POST   | /api/v1/auth/forgotPassword                     | Demande de réinitialisation du mot de passe |
|  11   |   PUT   | /api/v1/auth/resetPassword/{token}              | Réinitialisation de mot de passe         |
|  12   |  POST   | /api/v1/auth/addUserByAdmin                     | Ajout d'un utilisateur par un admin      |
|  13   |  POST   | /api/v1/plan/add                                | Ajout d'un plan                          |
|  14   |   PUT   | /api/v1/plan/update/{id}                        | Mise à jour d'un plan                    |
|  15   |   PUT   | /api/v1/plan/delete/{id}                        | Suppression d'un plan                    |
|  16   |   GET   | /api/v1/plan/all                                | Récupération de tous les plans           |
|  17   |  POST   | /api/v1/payment/create                          | Création d'un paiement                   |
|  18   |  POST   | /api/v1/payment/confirm                         | Confirmation d'un paiement               |
|  19   |  POST   | /api/v1/auth/user/registerBySubscription        | Inscription via abonnement               |
|  20   |  POST   | /api/v1/auth/loginGoogle                        | Connexion via Google                     |
|  21   |  POST   | /api/v1/auth/logout                             | Déconnexion utilisateur                  |
|  22   |  POST   | /api/v1/auth/admin/logout                       | Déconnexion administrateur               |
|  23   |   PUT   | /api/v1/auth/user/resendVerification            | Renvoyer l'email de vérification         |
|  24   |   PUT   | /api/v1/auth/user/disableAccount                | Désactivation du compte utilisateur      |
|  25   |  POST   | /api/v1/auth/user/reactivateAccount             | Réactivation du compte utilisateur       |
|  26   |   PUT   | /api/v1/auth/user/changePassword                | Changement de mot de passe               |
|  27   |  POST   | /api/v1/auth/user/updateEmail                   | Mise à jour de l'email utilisateur       |
|  28   |   PUT   | /api/v1/auth/admin/manageUsers                  | Gestion des utilisateurs par l'admin     |
|  29   |   PUT   | /api/v1/auth/admin/assignRole                   | Assignation de rôle                      |
|  30   |   PUT   | /api/v1/auth/admin/revokeRole                   | Révocation de rôle                       |
+-------+---------+------------------------------------------------+------------------------------------------+
```










# **Pourquoi un ordre précis pour les tests ?**
- L’objectif est de garantir que chaque fonctionnalité fonctionne correctement avant de passer à la suivante. 
- Tester les endpoints dans le bon ordre permet de :  

- **Éviter les erreurs bloquantes** en validant d'abord l'authentification.  
- **Assurer la cohérence des données** en testant progressivement la gestion des comptes et des plans.  
- **Faciliter le débogage** en isolant les erreurs à chaque étape.  
- **Garantir un parcours utilisateur fluide** pour les fonctionnalités comme l’inscription, la gestion des abonnements et le paiement.  

### **Outils requis pour les tests**
Avant de commencer, assurez-vous d’avoir :  
- **Swagger** pour tester les endpoints REST API.  
- **Postman (optionnel)** pour tester des cas avancés.  
- **Base de données accessible** pour vérifier les changements d’état des utilisateurs et des plans.  
- **Navigateur et outils de développement (F12)** pour tester l’intégration du localStorage et l’authentification.  

---
# **Ordre des Tests et Méthodologie**
---

Chaque test doit être effectué avec Swagger **avant** de développer l’interface.  

### **1. Authentification et Gestion des Comptes** (Tester en premier)  
💡 *Pourquoi ?*  
Sans authentification, il est impossible d’accéder aux autres fonctionnalités sécurisées.  

#### **Étape 1 : Tester l’inscription et la connexion pour un utilisateur normal**
1. **POST** `/api/v1/auth/user/register` – Créer un utilisateur normal.  
   - Envoyez les données requises (email, mot de passe, etc.).  
   - Vérifiez dans la base de données que l'utilisateur est bien enregistré.  
2. **PUT** `/api/v1/auth/validateAccount/{verificationCode}` – Vérifier le compte.  
   - Utilisez le code reçu par email pour activer le compte.  
   - Vérifiez que `is_validated = true` en base de données.  
3. **POST** `/api/v1/auth/token` – Connexion de l’utilisateur.  
   - Utilisez les identifiants pour récupérer un token d’authentification.  
   - **Stockez le token** dans le `localStorage` (via les outils du navigateur).  

#### **Étape 2 : Tester l’inscription et la connexion d’un administrateur**
1. **POST** `/api/v1/auth/admin/register` – Inscrire un administrateur.  
2. Modifier **manuellement** en base de données `is_validated = true`.  
3. **POST** `/api/v1/auth/token` – Connexion de l’admin.  
   - Vérifiez que le token est bien généré.  
4. **(Optionnel)** **PUT** `/api/v1/auth/validateAccount/{verificationCode}` – Si la validation admin est requise, tester cette API.  
5. **Ajout du superadmin** (MOHSEN1) : S'assurer que l'email `haythemrehouma@gmail.com` peut valider les administrateurs.  

---

### **2. Implémentation du Logout**
💡 *Pourquoi ?*  
Sans logout, les utilisateurs restent connectés indéfiniment et les tests d’authentification ne seront pas fiables.  

**Méthode de test :**  
1. **Supprimer le token du localStorage.**  
2. Vérifier que l’utilisateur n’a plus accès aux pages sécurisées.  
3. Ajouter un **bouton de déconnexion** sur l’interface.  

---

### **3. Connexion en tant qu’Administrateur**
💡 *Pourquoi ?*  
L’admin doit être authentifié pour gérer les plans.  

1. Se connecter avec l’admin via **POST** `/api/v1/auth/token`.  
2. Vérifier que les routes protégées de l’admin sont bien accessibles.  

---

### **4. Gestion des Plans** (Tester après l’authentification)
💡 *Pourquoi ?*  
L’utilisateur doit être connecté avant de gérer ses plans d’abonnement.  

#### **Méthode de test :**
1. **POST** `/api/v1/plan/add` – Ajouter un plan.  
   - Vérifier la création en base de données.  
2. **PUT** `/api/v1/plan/update/{id}` – Modifier un plan.  
   - Tester avec des valeurs différentes et valider la mise à jour.  
3. **PUT** `/api/v1/plan/delete/{id}` – Supprimer un plan.  
   - Vérifier que le plan est bien supprimé en base de données.  

#### **MOHSEN2 : Implémentation de la récupération des plans**
4. **GET** `/api/v1/plan/all` – Récupérer les plans disponibles.  
   - Vérifier que l’API retourne bien la liste des plans.  
   - Implémenter une interface permettant d’afficher ces plans (administrateur uniquement).  

---

### **5. Consultation de la Landing Page et Tarification**
💡 *Pourquoi ?*  
Un utilisateur non connecté doit pouvoir consulter les tarifs avant de souscrire.  

#### **Méthode de test :**
1. Vérifier que la **Landing Page** affiche les tarifs récupérés via **GET** `/api/v1/plan/all`.  
2. Ajouter un bouton pour souscrire à un plan.  

---

### **6. Gestion des Paiements** (Tester en dernier)
💡 *Pourquoi ?*  
Le paiement dépend des comptes et des plans. Il faut donc les tester en dernier.  

#### **Méthode de test :**
1. **POST** `/api/v1/payment/create` – Créer un paiement.  
   - Vérifier que le paiement est bien enregistré en base de données.  
2. **POST** `/api/v1/payment/confirm` – Confirmer un paiement.  
   - Vérifier que l’état du paiement passe à "Confirmé".  

⚠ **Vérification importante :**  
- Vérifier que la **référence du plan choisi** est bien envoyée au backend.  
- Simuler un cas d’échec (exemple : paiement refusé) et voir comment l’API réagit.  

---

### **7. Inscription via un Abonnement**
💡 *Pourquoi ?*  
Un utilisateur peut s’inscrire directement en souscrivant à un plan.  

#### **Méthode de test :**
1. **POST** `/api/v1/auth/user/registerBySubscription` – Inscription avec abonnement.  
   - Vérifier que l’utilisateur est bien enregistré et lié à un plan.  
   - Confirmer que le token de souscription est bien utilisé.  

#### **MOHSEN3 : Cas particulier**
2. Gérer le **renouvellement d’abonnement** pour un utilisateur déjà inscrit.  
3. Ajouter une gestion des remboursements (**refund**).  

---

### **8. Autres Fonctionnalités**
💡 *Pourquoi ?*  
Ces fonctionnalités permettent d’améliorer l’expérience utilisateur.  

#### **Validation et Gestion du Compte**
- **GET** `/api/v1/auth/userinsesson` – Vérifier l’utilisateur en session.  
- **PUT** `/api/v1/auth/updateAccount` – Modifier un compte utilisateur.  
- **POST** `/api/v1/auth/forgotPassword` – Réinitialisation du mot de passe (sans login).  
- **PUT** `/api/v1/auth/resetPassword/{token}` – Réinitialiser avec un token.  
- **PUT** `/api/v1/auth/deleteUser` – Suppression d’un compte (admin uniquement).  

#### **Gestion par un Administrateur**
- **POST** `/api/v1/auth/addUserByAdmin` – Ajouter un utilisateur depuis l’interface admin.  

---

### **9. Connexion via Google**
💡 *Pourquoi ?*  
Certains utilisateurs peuvent vouloir se connecter sans créer de compte.  

- **POST** `/api/v1/auth/loginGoogle` – Tester la connexion via Google.  
- Vérifier que le compte est bien créé après la première connexion.  

---

## **Résumé de la Stratégie de Test**
1. **Tester l’authentification en premier**, car elle conditionne l’accès aux autres fonctionnalités.  
2. **Tester la gestion des comptes** (modification, récupération de mot de passe).  
3. **Tester la gestion des plans** après l’authentification.  
4. **Enfin, tester les paiements**, car ils dépendent des plans et de l’authentification.  

Ce processus garantit des tests progressifs et efficaces, facilitant l’identification des erreurs à chaque étape.



