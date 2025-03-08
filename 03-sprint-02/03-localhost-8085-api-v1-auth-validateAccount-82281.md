# **1️⃣ Tester avec VS Code (REST Client)** 
Crée un fichier **`validate.http`** ou **`validate.rest`** et ajoute la requête suivante :

```http
PUT http://localhost:8085/api/v1/auth/validateAccount/82281
Content-Type: application/json
```
💡 **Remplace `82281`** par le **vrai code reçu** par l'utilisateur.

### 📌 **Étapes :**
1. **Installe l'extension REST Client** si ce n'est pas encore fait.
2. **Crée le fichier `.http` ou `.rest`**.
3. **Ouvre le fichier et clique sur "Send Request"**.


# **2️⃣ Tester avec cURL (Terminal / CMD)**
### 📌 **Commande corrigée :**
```sh
curl -X PUT "http://localhost:8085/api/v1/auth/validateAccount/82281" \
     -H "Content-Type: application/json"
```
💡 **Remplace `82281`** par le vrai code.

### 📌 **Exécution :**
- **Windows (CMD/Powershell)** : Exécute directement la commande.
- **Linux/Mac** : Exécute la commande dans le terminal.



# **3️⃣ Tester avec Fetch API (JavaScript)**
### 📌 **Code JavaScript corrigé :**
```js
const verificationCode = "82281"; // Remplace par le vrai code

fetch(`http://localhost:8085/api/v1/auth/validateAccount/${verificationCode}`, {
    method: "PUT",
    headers: {
        "Content-Type": "application/json"
    }
})
.then(response => response.json())
.then(data => console.log("Compte validé:", data))
.catch(error => console.error("Erreur:", error));
```
### 📌 **Exécuter le script :**
- **Dans le navigateur (F12 -> Console)** : Copie-colle le code.
- **Dans Node.js :**  
  1. **Crée un fichier** `validate.js` et colle le code.
  2. **Exécute :**  
     ```sh
     node validate.js
     ```


# ✅ **Conclusion**
| Méthode       | Utilisation                        | Idéal pour |
|--------------|---------------------------------|------------|
| **REST Client (VS Code)** | Interface graphique simple | Développement & tests rapides |
| **cURL (Terminal)** | Exécution en ligne de commande | Automatisation & scripts |
| **Fetch API (JavaScript)** | Côté client & backend Node.js | Développement web & front-end |

