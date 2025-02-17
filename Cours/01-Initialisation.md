## Mise en place de l’environnement PHP

## **1. Prérequis**

Avant d’installer Laravel, il faut s’assurer que l’environnement de développement est bien configuré. Voici les outils indispensables :

### **a) PHP et ses extensions**

Laravel nécessite PHP 8.1 ou une version supérieure. Pour vérifier la version installée, utilisez la commande :

```
php -v
```

Laravel nécessite également certaines extensions PHP :

- OpenSSL
- PDO
- Mbstring
- Tokenizer
- XML
- Ctype
- JSON
- BCMath
- Fileinfo

Vous pouvez vérifier les extensions activées avec :

```
php -m
```

Si certaines extensions sont manquantes, il faudra les activer dans le fichier php.ini.

### **b) Composer (Gestionnaire de dépendances PHP)**

Laravel utilise **Composer** pour gérer ses dépendances. Pour vérifier s’il est installé :

```
composer -v
```

Si ce n’est pas le cas, vous pouvez l’installer en le téléchargeant depuis [https://getcomposer.org](https://getcomposer.org/) et en exécutant le script d’installation.

### **c) Base de données**

Laravel supporte plusieurs bases de données, notamment :

- **MySQL**
- **PostgreSQL**
- **SQLite**
- **SQL Server**

L’outil le plus courant est **MySQL**. Vous pouvez utiliser **phpMyAdmin** ou **Adminer** pour gérer la base de données visuellement.

### **d) Node.js et NPM (Facultatif)**

Si vous utilisez **Vite** pour compiler les assets (CSS/JS), **Node.js** et **NPM** seront nécessaires :

```
node -v
npm -v
```

Si non installés, ils peuvent être téléchargés depuis [https://nodejs.org](https://nodejs.org/).

## **2. Installation de Laravel**

Une fois les prérequis en place, il est possible d’installer Laravel.

### **a) Installation via Composer**

Exécutez la commande suivante pour créer un nouveau projet Laravel :

```
composer create-project --prefer-dist laravel/laravel nom-du-projet

```

ou utilisez l’installeur Laravel :

```
composer global require laravel/installer
laravel new nom-du-projet

```

## **3. Configuration de l’environnement**

### **a) Configuration du fichier `.env`**

Laravel utilise un fichier **.env** pour gérer les configurations d’environnement, notamment :

- Connexion à la base de données
- Configuration du serveur mail
- Clé de l’application

Après installation, copiez le fichier `.env.example` en `.env` et générez la clé d’application :

```
cp .env.example .env
php artisan key:generate

```

### **b) Configuration de la base de données**

Dans `.env`, ajustez les paramètres selon votre base de données :

```
DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=nom_de_la_base
DB_USERNAME=root
DB_PASSWORD=

```

## **4. Lancer le serveur local**

Laravel intègre un serveur de développement. Pour le lancer :

```
php artisan serve
```

Cela démarre un serveur sur `http://127.0.0.1:8000`.

## **5. Vérification de l’installation**

Une fois le serveur lancé, ouvrez le navigateur et accédez à `http://127.0.0.1:8000`. Vous devriez voir la page d’accueil de Laravel.

## **6. Outils complémentaires**

### **a) Laravel Sail (Docker)**

Si vous voulez utiliser Docker pour un environnement unifié, **Laravel Sail** est une solution clé en main :

```
composer require laravel/sail --dev
php artisan sail:install
./vendor/bin/sail up

```

### **b) IDE et extensions**

Il est conseillé d’utiliser **VS Code** ou **PHPStorm** avec les extensions :

- Laravel Extension Pack (VS Code)
- Laravel IntelliSense
- PHP Intelephense

## **WAMP, MAMP, LARAGON, HERD : C'est quoi ?**

Ces outils sont des **serveurs locaux** qui regroupent plusieurs composants nécessaires à Laravel : **PHP, MySQL, Apache/Nginx, et parfois Composer**. Leur but est de faciliter la configuration et la gestion de l’environnement de développement.

| Outil | Plateforme | Serveur Web | Base de données | Points forts |
| --- | --- | --- | --- | --- |
| **WAMP** | Windows | Apache | MySQL/MariaDB | Populaire, stable, bien documenté |
| **MAMP** | macOS/Windows | Apache/Nginx | MySQL | Simple, inclut PHP et phpMyAdmin |
| **Laragon** | Windows | Nginx/Apache | MySQL/MariaDB/PostgreSQL | Léger, rapide, facile à configurer |
| **Herd** | macOS/Windows | Nginx | Pas de base intégrée | Minimaliste, dédié à Laravel |