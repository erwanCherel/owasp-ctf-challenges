# Étape 15 — XaSSebook_5

## Objectif
Fournir un lien valide sur l'application qui génère une alerte JavaScript au clic.

## Faille / Catégorie OWASP
**CWE-79: Cross-Site Scripting (XSS)**

## Démarche d'exploitation
Dans cette version, les chevrons sont échappés et le code est intégré à l'attribut `title` d'un tag `<a>` :

```html
<a href="#" title="FORBIDDENbutton onclick="alert('hello world!')"...">...</a>
```

L'application échappe les chevrons mais pas les guillemets à l'intérieur de l'attribut `title`. Il est donc possible de fermer prématurément l'attribut en ajoutant un guillemet au début du payload :

```
"<button onclick="alert('Hello World!')">Test</button>
```

Le guillemet initial ferme l'attribut `title`, ce qui permet d'injecter du HTML valide dans la page.

## Recommandations
- Échapper l'ensemble des caractères spéciaux (chevrons ET guillemets) via `htmlentities()` en PHP, avec le flag `ENT_QUOTES`

## Lien valide
```
"<button onclick="alert('Hello World!')">Test</button>
```
