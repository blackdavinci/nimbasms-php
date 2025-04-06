# Let's create the README.md file with the content provided.

readme_content = """
# NimbaSMS PHP Client

Un client PHP pour intégrer facilement l'API Nimba SMS à votre application, permettant l'envoi de SMS, la gestion des contacts et la vérification du solde.

## Table des matières
1. [Installation](#installation)
2. [Configuration](#configuration)
3. [Utilisation](#utilisation)
   - [Envoyer un SMS](#envoyer-un-sms)
   - [Gérer les contacts](#gérer-les-contacts)
   - [Vérifier le solde](#vérifier-le-solde)
   - [Récupérer l'historique des messages](#récupérer-lhistorique-des-messages)
4. [Enregistrement automatique avec Laravel](#enregistrement-automatique-avec-laravel)
5. [Licences](#licence)

---

## Installation

### 1. **Installer via Composer**

Vous pouvez installer le package via Composer en l'ajoutant directement à votre fichier `composer.json` ou en utilisant la commande suivante :

```bash
composer require blackdavinci/nimbasms-php
```

### 2. **Ajouter la clé API dans .env (si vous utilisez Laravel)**

Dans votre fichier .env, ajoutez la clé API fournie par Nimba SMS :

```env
NIMBA_SMS_API_KEY=your_api_key_here
```

### 3. **Configuration dans un projet PHP standard**

Si vous utilisez un projet PHP non Laravel, vous pouvez configurer la clé API dans un fichier config.php :

```php
<?php
// config.php
return [
    'api_key' => 'your_api_key_here',
    'api_url' => 'https://api.nimbasms.com/',
];
```

---

## Configuration

### **Laravel**

1. **Enregistrer le ServiceProvider** (automatiquement via `Package Discovery`).
   - Il n'y a rien à faire manuellement dans `config/app.php` si vous utilisez **Laravel Package Discovery**.
   - Laravel détectera automatiquement le **`NimbaSMSServiceProvider`** lors de l'installation.

2. **Utilisation dans votre application Laravel** : Vous pouvez maintenant injecter **`NimbaSMSClient`** dans vos contrôleurs.

### **PHP standard**

Dans un projet PHP standard, vous devez utiliser **`DependencyContainer`** pour enregistrer les services. Assurez-vous que **`config.php`** est correctement configuré.

## Utilisation

### **Envoyer un SMS**

Pour envoyer un SMS, utilisez la méthode **`sendMessage`**.

#### Exemple dans Laravel :
```php
use Blackdavinci\NimbasmsPhp\NimbaSMSClient;

class SmsController extends Controller
{
    public function send(NimbaSMSClient $client)
    {
        $response = $client->sendMessage('1234567890', 'Message de test');
        return response()->json($response);
    }
}
```

#### Exemple dans un projet PHP standard :
```php
require_once 'vendor/autoload.php';
$config = require 'config.php';

use Blackdavinci\NimbasmsPhp\NimbaSMSClient;

$client = new NimbaSMSClient($config['api_key']);
$response = $client->sendMessage('1234567890', 'Message de test');
echo json_encode($response);
```

### **Gérer les contacts**

#### Ajouter un contact :

```php
$response = $client->addContact('John Doe', '1234567890');
```

#### Lister les contacts :

```php
$response = $client->listContacts();
```

#### Supprimer un contact :

```php
$response = $client->deleteContact($contactId);
```

#### Mettre à jour un contact :

```php
$response = $client->updateContact($contactId, 'New Name', '0987654321');
```
### **Vérifier le solde**

Pour vérifier le solde de votre compte Nimba SMS :

```php
$response = $client->checkBalance();
```

### **Récupérer l'historique des messages **

Pour obtenir l'historique des messages envoyés :

```php
$response = $client->getMessageHistory('2023-01-01', '2023-12-31');
```

## Enregistrement automatique avec Laravel

Lorsque vous installez ce package via Composer, Laravel **enregistre automatiquement** le **`NimbaSMSServiceProvider`** grâce à la fonctionnalité de **Package Discovery**. Vous n'avez pas besoin de modifier manuellement le fichier **`config/app.php`**.

Laravel va automatiquement configurer l'accès à **NimbaSMSClient** dans vos contrôleurs via l'injection de dépendance.

---

## Licence

Ce package est distribué sous la licence **MIT**. Consultez le fichier `LICENSE` pour plus de détails.
