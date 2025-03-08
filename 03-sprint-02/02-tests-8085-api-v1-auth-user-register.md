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


# **2️⃣ Tester avec cURL (Terminal / CMD)**
**cURL** est un outil pour exécuter des requêtes HTTP en ligne de commande.

### **📌 Commande :**
```sh
curl -X POST "http://localhost:8085/api/v1/auth/user/register" \
     -H "Content-Type: application/json" \
     -d '{
           "firstName": "haythem",
           "lastName": "rehouma",
           "email": "rhoumahaythem@gmail.com",
           "password": "Spring123$",
           "phone": "4383504391",
           "profilePicture": "string",
           "roleTypes": "USER"
         }'
```
### **📌 Exécuter la commande :**
- **Windows (CMD/Powershell)** : Ajoute `^` à chaque ligne pour éviter d'erreurs.
- **Linux/Mac** : Exécute directement dans un terminal.


# **3️⃣ Tester avec Fetch API (JavaScript)**
La **Fetch API** permet d'exécuter des requêtes HTTP côté client ou backend.

### **📌 Code JavaScript :**
```js
fetch("http://localhost:8085/api/v1/auth/user/register", {
    method: "POST",
    headers: {
        "Content-Type": "application/json"
    },
    body: JSON.stringify({
        firstName: "haythem",
        lastName: "rehouma",
        email: "rhoumahaythem@gmail.com",
        password: "Spring123$",
        phone: "4383504391",
        profilePicture: "string",
        roleTypes: "USER"
    })
})
.then(response => response.json())
.then(data => console.log(data))
.catch(error => console.error("Error:", error));
```

# **📌 Exécuter le script :**
- **Dans le navigateur (F12 -> Console)** : Copie-colle le code.
- **Dans Node.js :**  
  1. **Crée un fichier** `test.js` et colle le code.
  2. **Exécute :**  
     ```sh
     node test.js
     ```


## **✅ Conclusion**
| Méthode       | Utilisation                        | Idéal pour |
|--------------|---------------------------------|------------|
| **REST Client (VS Code)** | Simple et rapide avec une interface graphique | Développement et tests rapides |
| **cURL (Terminal)** | Exécution en ligne de commande | Automatisation & scripts |
| **Fetch API (JavaScript)** | Exécution côté client et backend Node.js | Développement web et front-end |

