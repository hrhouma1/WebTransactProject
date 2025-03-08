ghp_FwgTbTOBsQBCr3txeSFAyDDXCUlbZy01wA-H
---
# ÉTAPE 1 - Création du projet
---

```python
mkdir newtechmindv1
cd newtechmindv1
npm create vite@latest . -- --template react-ts
npm install -D tailwindcss postcss autoprefixer
npx tailwind init -p
npm install -D tailwindcss@3 postcss autoprefixer
npx tailwind init -p
npm run dev
code .
doskey /history
# Références
# https://medium.com/@pushpendrapal_/how-to-setup-react-typescript-and-tailwind-css-with-vite-in-a-project-8d9b0b51d1bd
# https://www.youtube.com/watch?v=5m9jkqXEc28
```

---
# ÉTAPE 2. SÉRIE 1 de Prompts à donner à Cursor AI (CRTL + I) ( Série 1 ==> 2, 3, 4)
---

# 2.1

### **🚀 Prompt pour Cursor AI : Développement d'une interface React pour l'authentification**  

> **Prompt :**
>  
> **Objectif :** Développe une interface **React** permettant l'inscription, la validation de compte et l'authentification d'un utilisateur via une API REST.  
>  N'oublie pas que j'utilise TypeScript, React et Tailwind.
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

# 2.2

# Partie 1 - développer l'interface correpondante



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



# Partie 2 - développer l'interface correpondante

```http
PUT http://localhost:8085/api/v1/auth/validateAccount/82281
Content-Type: application/json
```


### Partie 3 - développer l'interface correpondante


L'endpoint `/api/v1/auth/token` permet à l'utilisateur de s'authentifier et de recevoir un **JWT Token** qu'il pourra utiliser pour les requêtes sécurisées.


```http
POST http://localhost:8085/api/v1/auth/token
Content-Type: application/json

{
  "email": "rhoumahaythem@gmail.com",
  "password": "Spring123$"
}
```

# 2.3 - Insistez pour utiliser ces technologies et ne pas utiliser javascript mais plutôt TypeScript

- N'oublie pas que j'utilise TypeScript, React et Tailwind.





---
# ÉTAPE 3. SÉRIE 2 de Prompts - Raffinements de prompts
---

*J'ai donné le prompt générale plusieurs fois et le problème a été fixé !*

**Prompt 1  Générale:**  
*"Mon application utilise TypeScript, React et Tailwind, mais certains éléments ne s'affichent pas correctement sur la page. Peux-tu analyser le CSS appliqué aux composants et identifier les problèmes potentiels ? Voici quelques détails :*  

**Peux-tu m'aider à diagnostiquer et résoudre ce problème ?



*OPTIONNEL*

**Prompt 2 spécifique:**  
*"Mon application utilise TypeScript, React et Tailwind, mais certains éléments ne s'affichent pas correctement sur la page. Peux-tu analyser le CSS appliqué aux composants et identifier les problèmes potentiels ? Voici quelques détails :*  

- *Les styles Tailwind sont bien appliqués dans le JSX, mais l'affichage ne correspond pas aux attentes.*  
- *Certains éléments sont invisibles ou mal positionnés.*  
- *J'utilise `className` correctement dans mes composants React.*  
- *J'ai vérifié que Tailwind est bien importé dans mon projet.*  

**Peux-tu m'aider à diagnostiquer et résoudre ce problème ? Je peux te fournir le code d'un composant spécifique si nécessaire.**"  



---
# ÉTAPE 4. Accéder à la page
---

*Vérifiez les composants*

- http://localhost:5173/
- http://localhost:5173/register
- http://localhost:5173/login


---
# ÉTAPE 5. Travaillez avec git
---


```bash
# Initialiser un dépôt Git
git init

# Ajouter tous les fichiers au suivi
git add .

# Configurer le nom d'utilisateur localement
git config --local user.name "hrhouma1"

# Configurer l'email localement
git config --local user.email "rhoumahaythem@gmail.com"

# Commiter les modifications avec un message
git commit -m "Initial commit"

# Ajouter un dépôt distant (remplacez l'URL par celle de votre repo)
git remote add origin https://github.com/hrhouma1/sw1.git
git branch -M main
git push -u origin main

```

🔹 **Explication des corrections :**  
- `git config username --local` → remplacé par `git config --local user.name "VotreNomUtilisateur"`.
- `git config email --local` → remplacé par `git config --local user.email "VotreEmail@example.com"`.
- Ajout du commit (`git commit -m "message"`) car `git push` nécessite des commits.
- Ajout du dépôt distant avec `git remote add origin` avant le `git push`.
- `git push -u origin main` permet de lier la branche locale à la branche distante.

Si votre branche principale s'appelle `master` au lieu de `main`, adaptez la dernière commande avec :
```bash
git push -u origin master
```



---
# ÉTAPE 6. Cloner le projet sur la VM Ubuntu 2204
---

```bash
git clone https://github.com/hrhouma1/sw1.git
cd sw1
code .
npm install
npm run dev
```


---
# ÉTAPE 7. Cloner le projet sur la VM Ubuntu 2204
---

```bash
testez http://localhost:5173/register

```
### Erreur

```ssh
Cross-Origin Request Blocked: The Same Origin Policy disallows reading the remote resource at http://localhost:8085/api/v1/auth/user/register. (Reason: CORS header ‘Access-Control-Allow-Origin’ missing). Status code: 403.  Cross-Origin Request Blocked: The Same Origin Policy disallows reading the remote resource at http://localhost:8085/api/v1/auth/user/register. (Reason:
```

```ssh
CORS request did not succeed). Status code: (null). insiste su r TypeScript, React et Tailwind.
```


---
# ÉTAPE 8. Cloner le projet sur la VM Ubuntu 2204
---

> **Prompt :**
>  

Je travaille sur une application frontend avec **TypeScript, React et Tailwind CSS**, qui communique avec un backend à l'URL **http://localhost:8085/api/v1/auth/user/register**.  

J'obtiens une erreur CORS :  

**Cross-Origin Request Blocked: The Same Origin Policy disallows reading the remote resource at http://localhost:8085/api/v1/auth/user/register. (Reason: CORS header ‘Access-Control-Allow-Origin’ missing). Status code: 403.**  
**Cross-Origin Request Blocked: The Same Origin Policy disallows reading the remote resource at http://localhost:8085/api/v1/auth/user/register. (Reason: CORS request did not succeed). Status code: (null).**  

Peux-tu corriger cela en modifiant mon backend pour ajouter les bons en-têtes CORS ? Assure-toi que :  
- **Le backend autorise les requêtes venant de `http://localhost:5173`** (si j'utilise Vite) ou `http://localhost:3000` (si j'utilise Create React App).  
- **Les méthodes HTTP nécessaires sont bien autorisées (GET, POST, PUT, DELETE, OPTIONS)**.  
- **Les headers `Content-Type` et `Authorization` sont acceptés**.  
- **La configuration fonctionne correctement pour une API REST utilisée avec un frontend React en TypeScript**.  

Donne-moi une solution spécifique en fonction du backend possible : **Express.js (Node.js), NestJS, Spring Boot ou Django**.  
Ajoute les commandes nécessaires si je dois installer un package (`cors`, `django-cors-headers`, etc.).  

Merci ! 🚀  
