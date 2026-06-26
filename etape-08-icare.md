# Étape 08 — Icare

## Objectif
Se connecter en admin. Le fichier source `index.php.txt` est disponible.

## Faille / Catégorie OWASP
**A01:2021 – Broken Access Control**

## Démarche d'exploitation
1. Accès à `index.php.txt` → source du fichier `index.php`
2. Lecture du code : les variables `login` et `pass` saisies via le formulaire servent à déclarer une variable `admin` et lui assigner la valeur `1`
3. Il est donc possible de tromper le formulaire en soumettant directement la variable `admin` sans renseigner login ni mot de passe

Injection via l'ajout d'un champ caché dans le formulaire :
```html
<td><input name="admin" type="admin" value="1"></td>
```

## Recommandations
- Implémenter un système de tokens CSRF pour prévenir les attaques de falsification de requête intersite
- Valider et nettoyer les données avant traitement (ex. `FILTER_SANITIZE_` en PHP)
- Utiliser un algorithme de hachage robuste pour les mots de passe (Argon2 ou Bcrypt plutôt que SHA-1)

## Certificat
`80ac3c52ab29642baf44f157ffeabe33cc09662030fb06a2b296adbb543f5b5098421ddd124e1ad9`
