# Étape 13 — XaSSebook_1

## Objectif
Fournir un lien valide sur l'application qui génère une alerte JavaScript au clic.

## Faille / Catégorie OWASP
**CWE-79: Cross-Site Scripting (XSS)**

## Démarche d'exploitation
La barre de recherche accepte directement des tags HTML sans échappement. Le payload suivant suffit :

```html
<button onclick="alert('You\'ve been hacked!')">Faites moi confiance : cliquez !</button>
```

Le lien généré par l'application, contenant ce payload dans l'URL, peut être partagé et déclenchera l'alerte chez tout utilisateur qui clique dessus.

## Recommandations
- Échapper les caractères spéciaux et les convertir en entités HTML via `htmlentities()` ou `htmlspecialchars()` en PHP avant d'afficher tout contenu issu de l'utilisateur

## Lien valide
```
<button onclick="alert('You\'ve been hacked!')">Faites moi confiance : cliquez !</button>
```
