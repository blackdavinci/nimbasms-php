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

### 2. Ajouter la clé API dans .env (si vous utilisez Laravel)

Dans votre fichier `.env`, ajoutez la clé API fournie par Nimba SMS :

```env
NIMBA_SMS_API_KEY=your_api_key_here

