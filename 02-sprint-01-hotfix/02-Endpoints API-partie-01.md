# **Ordre des tests des Endpoints**  

# **1. Authentification et gestion des comptes (Tester en premier)**  

**Objectif** : Vérifier que l'authentification et la gestion des utilisateurs fonctionnent avant de passer aux autres fonctionnalités.  

- Tester avec **Swagger** dans un premier temps.  
- Développer les interfaces suivantes :  
  - Inscription (`Register`)  
  - Connexion (`Login`)  
  - Confirmation (`Email Verification`)  
  - Page d'accueil (`Landing Page`)  

- Un **utilisateur administrateur** doit avoir accès à une **interface supplémentaire** :  
  - Page administrative pour la gestion des plans  

### **1.1 Inscription et authentification d'un utilisateur normal**  

- **POST** `/api/v1/auth/user/register` – Inscription d’un nouvel utilisateur  
- **PUT** `/api/v1/auth/validateAccount/{verificationCode}` – Validation du compte avec un code de vérification  
- **POST** `/api/v1/auth/token` – Récupération d’un token d’authentification  

### **1.2 Inscription et authentification d’un administrateur**  

- **POST** `/api/v1/auth/admin/register` – Inscription d’un administrateur  
- Modifier directement dans la base de données l’attribut `is_validated` à `true` dans la table `user`  
- **POST** `/api/v1/auth/token` – Récupération d’un token d’authentification  

### **1.3 Validation optionnelle d’un administrateur**  

---
# NEW FIX 1
---

- *J'ai ajouté l’email du **superadmin** `haythemrehouma@gmail.com` pour valider les comptes administrateurs.* 

- **PUT** `/api/v1/auth/validateAccount/{verificationCode}` – Validation du compte administrateur via un email  






<br/>
<br/>
<br/>

# **2. Implémentation du logout**  

- **Pas besoin d’API**. Supprimer le **token du `localStorage`** côté client.  
- Vérifier manuellement dans le navigateur que le token est bien supprimé.  
- Développer une interface avec un **bouton de déconnexion**.  





<br/>
<br/>
<br/>

# **3. Connexion en tant qu’administrateur**  

Pré-requis pour pouvoir gérer les plans.  





<br/>
<br/>
<br/>

# **4. Gestion des plans (Tester après l’authentification)**  

**Objectif** : Une fois connecté, un utilisateur peut gérer ses plans.  

### **4.1 Création et gestion des plans**  

- **POST** `/api/v1/plan/add` – Ajouter un nouveau plan  
- **PUT** `/api/v1/plan/update/{id}` – Modifier un plan existant  
- **PUT** `/api/v1/plan/delete/{id}` – Supprimer un plan  
- **GET** `/api/v1/plan/all` – Récupérer la liste des plans *(MOSEN2 – Ajout du GET)*  

**Détails** :  
- Tester avec **Swagger** avant de développer l’interface.  
- Un **administrateur** doit gérer cette partie.  
- Développer **une seule interface** pour la gestion des plans.  




<br/>
<br/>
<br/>

# **5. Vérification du logout après connexion**  

S’assurer que la déconnexion est bien gérée après authentification.  


<br/>
<br/>
<br/>

# **6. Landing page et affichage des tarifs**  

Le client non connecté doit pouvoir consulter les tarifs et choisir un plan.  


<br/>
<br/>
<br/>

# **7. Gestion des paiements (Tester en dernier)**  

**Objectif** : Une fois les plans prêts, tester le processus de paiement.  

### **7.1 Effectuer un paiement**  

- **POST** `/api/v1/payment/create` – Création d’un paiement  
- **POST** `/api/v1/payment/confirm` – Confirmation d’un paiement  

**Détails** :  
- Vérifier les **paramètres envoyés**, notamment la **référence du plan** choisi.  
- Tester avec **Swagger** avant d’implémenter l’interface.  


<br/>
<br/>
<br/>

# **8. Gestion des abonnements et cas particuliers**  

### **8.1 Inscription via un abonnement (Nouvel utilisateur)**  

- **POST** `/api/v1/auth/user/registerBySubscription` – Inscription avec abonnement  

**Détails** :  
- Cette action **redirige vers la page d’inscription** avec un **token de souscription**.  

### **8.2 Renouvellement d’un abonnement pour un utilisateur déjà inscrit**  

(*OPTIONNEL - Prochains sprints*) Gérer le cas où un utilisateur déjà connecté souhaite renouveler son abonnement.  

- Implémenter la **gestion des remboursements** (`refund`).  

<br/>
<br/>
<br/>

# **9. Autres fonctionnalités**  

### **9.1 Validation et gestion du compte**  

- **GET** `/api/v1/auth/userinsesson` – Vérifier l’utilisateur en session (*test via Swagger uniquement, pas d’interface requise*)  
- **PUT** `/api/v1/auth/updateAccount` – Mettre à jour les informations du compte (*admin et utilisateur normal, avec interface*)  
- **POST** `/api/v1/auth/forgotPassword` – Demander une réinitialisation de mot de passe (*sans connexion, avec interface*)  
- **PUT** `/api/v1/auth/resetPassword/{token}` – Réinitialiser le mot de passe (*sans connexion, avec interface*)  
- **PUT** `/api/v1/auth/deleteUser` – Supprimer un compte utilisateur (*uniquement pour l’administrateur*)  

### **9.2 Gestion des utilisateurs par un administrateur**  

- **POST** `/api/v1/auth/addUserByAdmin` – Ajout d’un utilisateur par un administrateur (*interface à développer dans le back-office*)  

### **9.3 Connexion via Google**  

- **POST** `/api/v1/auth/loginGoogle` – Connexion avec un compte Google  



## **Explication de la stratégie**  

1. **Tester l’authentification en premier** (impossible d’accéder aux autres fonctionnalités sécurisées sans cela).  
2. **Gérer les comptes et utilisateurs** (modification du profil, récupération de mot de passe).  
3. **Tester la gestion des plans** (création, modification, suppression).  
4. **Enfin, tester les paiements** (car ils dépendent des comptes et des plans).  


## **Résumé de l’ordre des tests des endpoints**  

### **Phase 1 : Authentification**  
- Inscription utilisateur  
- Validation du compte  
- Connexion utilisateur  
- Inscription administrateur  
- Validation administrateur  
- Connexion administrateur  
- Implémentation du logout  

### **Phase 2 : Gestion des comptes**  
- Vérification de l’utilisateur en session  
- Mise à jour des informations  
- Réinitialisation de mot de passe  
- Suppression de compte  

### **Phase 3 : Gestion des plans**  
- Ajouter un plan  
- Modifier un plan  
- Supprimer un plan  
- Récupérer les plans  

### **Phase 4 : Gestion des paiements**  
- Création d’un paiement  
- Confirmation d’un paiement  
- Inscription par abonnement  
- Renouvellement et remboursement  

