# **Tutoriel complet : Récupérer un Token après authentification**   

L'endpoint `/api/v1/auth/token` permet à l'utilisateur de s'authentifier et de recevoir un **JWT Token** qu'il pourra utiliser pour les requêtes sécurisées.


## **1️⃣ Tester avec VS Code (REST Client)**
Ajoute la requête suivante dans un fichier **`token.http`** ou **`token.rest`** :

```http
POST http://localhost:8085/api/v1/auth/token
Content-Type: application/json

{
  "email": "rhoumahaythem@gmail.com",
  "password": "Spring123$"
}
```
### **Étapes** :
1. **Installer l'extension REST Client** si ce n'est pas encore fait.
2. **Créer le fichier `.http` ou `.rest`**.
3. **Lancer la requête en cliquant sur "Send Request"**.



## **2️⃣ Tester avec cURL (Terminal / CMD)**
### **Commande :**
```sh
curl -X POST "http://localhost:8085/api/v1/auth/token" \
     -H "Content-Type: application/json" \
     -d '{
           "email": "rhoumahaythem@gmail.com",
           "password": "Spring123$"
         }'
```
### **Exécution :**
- **Windows (CMD/Powershell)** : Exécute directement.
- **Linux/Mac** : Exécute dans le terminal.



## **3️⃣ Tester avec Fetch API (JavaScript)**
### **Code JavaScript :**
```js
fetch("http://localhost:8085/api/v1/auth/token", {
    method: "POST",
    headers: {
        "Content-Type": "application/json"
    },
    body: JSON.stringify({
        email: "rhoumahaythem@gmail.com",
        password: "Spring123$"
    })
})
.then(response => response.json())
.then(data => {
    console.log("Token reçu:", data.jwtToken);
})
.catch(error => console.error("Erreur:", error));
```
### **Exécuter le script :**
- **Dans le navigateur (F12 -> Console)** : Copie-colle le code.
- **Dans Node.js :**  
  1. **Créer un fichier** `token.js` et y coller le code.
  2. **Exécuter la commande :**  
     ```sh
     node token.js
     ```



## **Exemple de Réponse JSON avec le Token**
Lorsqu'on envoie une requête valide, l'API retourne une réponse **200 OK** contenant le **JWT Token** :

```http
HTTP/1.1 200 OK
Vary: Origin, Access-Control-Request-Method, Access-Control-Request-Headers
X-Content-Type-Options: nosniff
X-XSS-Protection: 0
Cache-Control: no-cache, no-store, max-age=0, must-revalidate
Pragma: no-cache
Expires: 0
X-Frame-Options: DENY
Content-Type: application/json
Transfer-Encoding: chunked
Date: Sat, 08 Mar 2025 00:38:17 GMT
Connection: close
```
```json
{
  "user": {
    "email": "rhoumahaythem@gmail.com",
    "username": null,
    "firstName": "haythem",
    "lastName": "rehouma",
    "phoneNumber": null,
    "profilePicture": null,
    "roleTypes": "USER",
    "subscriptionList": [],
    "plan": null
  },
  "jwtToken": "eyJhbGciOiJIUzI1NiJ9.eyJyb2xlcyI6IlVTRVIiLCJlbWFpbCI6InJob3VtYWhheXRoZW1AZ21haWwuY29tIiwic3ViIjoicmhvdW1haGF5dGhlbUBnbWFpbC5jb20iLCJpYXQiOjE3NDEzOTQyOTcsImV4cCI6MTc0MTQwMTQ5N30.XswpOJQglsHteQde4AnG2RCRx-SCj8rF4d42h68RNq0"
}
```

## **Conclusion**
| Méthode       | Objectif                           | Idéal pour |
|--------------|---------------------------------|------------|
| **REST Client (VS Code)** | Tester rapidement dans une interface | Développement & tests rapides |
| **cURL (Terminal)** | Exécuter en ligne de commande | Automatisation & scripts |
| **Fetch API (JavaScript)** | Intégration dans une application web | Front-end & back-end Node.js |

