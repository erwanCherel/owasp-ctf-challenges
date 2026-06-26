# Étape 14 — XaSSebook_3

## Objectif
Fournir un lien valide sur l'application qui génère une alerte JavaScript au clic.

## Faille / Catégorie OWASP
**CWE-79: Cross-Site Scripting (XSS)**

## Démarche d'exploitation
Même vecteur que XaSSebook_1 — la barre de recherche accepte des tags HTML.

```html
<button onclick="alert('You\'ve been hacked for the second time!')">Faites moi confiance : cliquez !</button>
```

## Recommandations
- Échapper les caractères spéciaux via `htmlentities()` ou `htmlspecialchars()` en PHP avant tout affichage de contenu utilisateur

## Lien valide
```
<button onclick="alert('You\'ve been hacked for the second time!')">Faites moi confiance : cliquez !</button>
```
