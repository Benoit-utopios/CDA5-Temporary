# 2 - Découverte du router, des views et de Blade

## 1. Les Routes et le Router dans Laravel

## **A) Qu'est-ce qu'une Route dans Laravel ?**

Une **route** est un point d’entrée qui permet de répondre aux requêtes HTTP et de les diriger vers une logique spécifique (contrôleur, vue, ou réponse directe).

**📍 Emplacement des routes :**

Les routes sont définies dans **`routes/web.php`** pour les pages web et dans **`routes/api.php`** pour les API.

---

## **B) Types de routes**

### **1️⃣ Route basique**

Elle affiche directement un texte ou une vue.

```php
use Illuminate\Support\Facades\Route;

Route::get('/bonjour', function () {
    return 'Bonjour, bienvenue sur Laravel!';
});

```

### **2️⃣ Route vers une vue**

Une route peut renvoyer une **vue Blade** :

```php
Route::get('/accueil', function () {
    return view('accueil');
});

```

### **3️⃣ Route avec un paramètre**

On peut capturer une valeur passée dans l’URL :

```php
Route::get('/user/{id}', function ($id) {
    return "Utilisateur ID : " . $id;
});

```

👉 Accéder à `/user/5` affichera **"Utilisateur ID : 5"**.

### **4️⃣ Route vers un contrôleur**

Une bonne pratique consiste à déléguer la logique à un **contrôleur** :

```php
use App\Http\Controllers\UserController;

Route::get('/profil/{id}', [UserController::class, 'afficherProfil']);

```

# **2. Les Vues dans Laravel**

## **A) Qu'est-ce qu'une Vue ?**

Une **vue** est un fichier qui contient du code HTML (et Blade) permettant d’afficher une page à l’utilisateur.

**📍 Emplacement des vues :**

Les vues sont stockées dans **`resources/views/`**.

## **B) Affichage d'une Vue**

Dans une route ou un contrôleur, on affiche une vue avec `view()` :

```php
Route::get('/accueil', function () {
    return view('accueil');
});

```

Si le fichier **`resources/views/accueil.blade.php`** existe, il sera chargé.

## **C) Passer des données à une Vue**

On peut envoyer des données à une vue :

```php
Route::get('/accueil', function () {
    return view('accueil', ['nom' => 'Jean']);
});

```

Dans `resources/views/accueil.blade.php` :

```
<h1>Bienvenue,  {{ $nom }}</h1>
```

---

# **3. Blade : Le moteur de templates de Laravel**

Blade est le moteur de template de Laravel qui permet d’écrire du HTML avec des fonctionnalités dynamiques.

**📍 Tous les fichiers Blade sont en `.blade.php`**

Exemple : **`resources/views/accueil.blade.php`**

---

## **A) Syntaxe Blade**

### **1️⃣ Afficher une variable**

```
<p>Bonjour, {{ $nom }}</p>
```

### **2️⃣ Conditions avec `@if`**

```
@if($age >= 18)
    <p>Vous êtes majeur.</p>
@else
    <p>Vous êtes mineur.</p>
@endif

```

### **3️⃣ Boucles (`@foreach`, `@for`, `@while`)**

```
@foreach($utilisateurs as $utilisateur)
    <p>{{ $utilisateur->nom }}</p>
@endforeach

```