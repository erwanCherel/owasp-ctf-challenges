# Étape 07 — Calc v6

## Objectif
Lire le fichier `.htsecret`.

## Faille / Catégorie OWASP
**A03:2021 – Injection**

## Démarche d'exploitation
Dans cette version, les backticks sont également filtrés — les techniques des étapes 02 et 06 ne fonctionnent plus.

Hypothèse : le certificat est stocké dans une variable d'environnement (comme constaté à l'étape 03).

1. Tentative avec `getenv()` → non concluant
2. Consultation de la documentation PHP → `phpinfo()` permet de visualiser les variables d'environnement
3. Injection de `phpinfo()` dans l'input → le certificat est visible en face de la variable `STEP_TOKEN`

## Recommandations
- Restreindre l'accès à `phpinfo()` par adresse IP :
```php
if ($_SERVER['REMOTE_ADDR'] == '1.2.3.4') phpinfo();
```
- Désactiver `phpinfo()` dans `php.ini` via `disable_functions`

## Certificat
`e82f0dba8730daeffdeda8a18ae27f4bb2d538afad6817fd3f2a34aadfe134ef0e3f3dca1758592c`
