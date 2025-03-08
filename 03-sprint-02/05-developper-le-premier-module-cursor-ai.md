### **🚀 Prompt pour Cursor AI : Développement d'une interface React pour l'authentification**  

> **Prompt :**
>  
> **Objectif :** Développe une interface **React** permettant l'inscription, la validation de compte et l'authentification d'un utilisateur via une API REST.  
>  
> **Stack technique :** React (Vite ou Create React App), TypeScript, Tailwind CSS, Axios pour les requêtes API, React Router pour la navigation, Zustand ou Context API pour la gestion d'état.  
>  
> ### **📌 Fonctionnalités à implémenter :**
> 1️⃣ **Inscription d'un utilisateur (Register)**  
>   - Formulaire avec `firstName`, `lastName`, `email`, `password`, `phone`, `profilePicture`, `roleTypes`.  
>   - Requête `POST` vers `http://localhost:8085/api/v1/auth/user/register`.  
>   - Gestion des erreurs et affichage des messages de succès ou d’échec.  
>  
> 2️⃣ **Validation du compte avec un code reçu par email**  
>   - Champ pour entrer le `verificationCode`.  
>   - Requête `PUT` vers `http://localhost:8085/api/v1/auth/validateAccount/{verificationCode}`.  
>   - Gestion des erreurs et affichage du message de confirmation.  
>  
> 3️⃣ **Authentification (Login) et récupération du Token**  
>   - Formulaire avec `email` et `password`.  
>   - Requête `POST` vers `http://localhost:8085/api/v1/auth/token`.  
>   - Stockage du token JWT dans `localStorage`.  
>   - Redirection vers une page sécurisée après connexion.  
>  
> ### **📌 Structure des fichiers :**
> ```
> src/
> ├── components/
> │   ├── RegisterForm.tsx
> │   ├── ValidateAccount.tsx
> │   ├── LoginForm.tsx
> │   ├── ProtectedRoute.tsx  (Gère l'accès aux pages sécurisées)
> │   ├── Navbar.tsx
> ├── pages/
> │   ├── Home.tsx
> │   ├── Dashboard.tsx (Page accessible après connexion)
> │   ├── Login.tsx
> │   ├── Register.tsx
> │   ├── Validate.tsx
> ├── context/AuthContext.tsx  (Gestion de l'état utilisateur & token)
> ├── api/apiClient.ts  (Fichier pour les appels Axios)
> ├── App.tsx
> ├── main.tsx
> ```
>  
> **📌 Exigences supplémentaires :**
> - Utilisation de **React Hook Form** pour la gestion des formulaires.  
> - Validation des champs avec **Yup** ou **Zod**.  
> - Interface moderne avec **Tailwind CSS**.  
> - Utilisation de **React Router** pour la navigation.  
> - Stocker le **JWT Token** dans `localStorage` et gérer l'état utilisateur avec Context API ou Zustand.  
> - Gestion des erreurs avec `try/catch` et affichage des messages d’erreur en temps réel.  
>  
> **📌 Bonus :** Ajoute une redirection automatique vers `/dashboard` après une connexion réussie, et empêche l’accès aux routes protégées sans token.  



# Partie 1

# **Tester une requête POST avec 3 méthodes (VS Code, cURL, Fetch API)** 
# **1️⃣ Tester avec VS Code (REST Client)**
L'extension **REST Client** permet d'envoyer des requêtes HTTP directement dans **VS Code**.

### **📌 Étapes :**
1. **Installer l'extension REST Client** dans VS Code.
2. **Créer un fichier** avec l'extension `.rest` ou `.http` (ex: `test.http`).
3. **Ajouter la requête suivante :**

```http
POST http://localhost:8085/api/v1/auth/user/register
Content-Type: application/json

{
  "firstName": "haythem",
  "lastName": "rehouma",
  "email": "rhoumahaythem@gmail.com",
  "password": "Spring123$",
  "phone": "4383504391",
  "profilePicture": "string",
  "roleTypes": "USER"
}
```
4. **Exécuter la requête** :  
   - Ouvre le fichier `.http` dans VS Code.
   - Clique sur **"Send Request"**.


### Partie 2


### Partie 3
