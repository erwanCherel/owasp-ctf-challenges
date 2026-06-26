# Étape 01 — Javapass

## Objectif
Trouver le mot de passe.

## Faille / Catégorie OWASP
**A07:2021 – Identification and Authentication Failures**

## Démarche d'exploitation
Le mot de passe demandé par l'application est visible en clair dans la fonction d'évaluation du mot de passe, directement accessible dans le code JavaScript via un simple *clic droit > Inspecter* dans le navigateur.

## Recommandations
Déplacer la charge de l'évaluation du mot de passe du côté client au côté serveur via une requête HTTP POST, afin de confier au serveur la responsabilité de :
- retrouver l'utilisateur correspondant
- comparer les mots de passe
- retourner une réponse appropriée (401 Unauthorized / 200 OK)

Il est également préférable de hacher le mot de passe en amont de l'enregistrement, rendant son exploitation par un utilisateur malveillant très difficile.

## Certificat
`ccb7639a464c975b196c5fe00330086e62b2121794739008b249ffc520f478b9b073dcfbe9dccdb6`
