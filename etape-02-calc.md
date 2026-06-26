# Étape 02 — Calc

## Objectif
Lire le fichier `.htsecret`.

## Faille / Catégorie OWASP
**A03:2021 – Injection**

## Démarche d'exploitation
Le site est constitué d'un simple formulaire censé servir de calculatrice. La faille se situe au niveau de l'input : du code PHP est exécuté directement via une fonction `eval()`.

**Étapes :**
1. Test initial avec `alert("Hello World!")` → non concluant (JavaScript, pas PHP)
2. Test avec `print("Hello World!")` → retourne `Hello World!1` → confirmation d'exécution PHP via `eval()`
3. Localisation du fichier cible :
```php
$output = shell_exec('ls -lart');
echo "<pre>$output</pre>";
```
Résultat : présence de `.htsecret` dans le répertoire courant.

4. Lecture du fichier :
```php
file_get_contents('.htsecret')
```

## Recommandations
- S'assurer via une expression régulière que seuls des chiffres et opérations mathématiques sont acceptés dans l'input
- Éviter l'utilisation de la fonction `eval()`
- Utiliser une librairie PHP dédiée aux opérations arithmétiques (ex. MathPHP)

## Certificat
`a582fff49ba7fcb796201c725dadc28ef2faaaeafca0b5b9ad13f312031cd408d7a3be56f560bfca`
