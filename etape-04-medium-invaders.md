# Étape 04 — Medium Invaders

## Objectif
Remplir un certain nombre de fois le formulaire dans un temps limité (42 captchas en 42 secondes).

## Faille / Catégorie OWASP
**Cross-Site Request Forgery (CSRF)**

## Démarche d'exploitation
1. Soumission du formulaire une première fois
2. Retour en arrière dans le navigateur → constat : le captcha est identique
3. Nouvelle soumission → le compteur passe de 0 à 1
4. Répétition de l'opération jusqu'à atteindre 42

L'absence de token CSRF et l'absence d'invalidation du captcha après soumission permettent de rejouer indéfiniment la même requête.

## Recommandations
- Générer un token CSRF unique associé à chaque formulaire
- Vérifier le captcha et le token CSRF côté serveur lors de l'envoi du formulaire
- Invalider le captcha et le token après soumission pour empêcher leur réutilisation

## Certificat
`4a6f5aa374b40e339bd548871d16785b8e2c58788fa34b91b8f720e69bb971a45c8aaedc9b11acd4`
