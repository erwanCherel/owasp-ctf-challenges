# Étape 11 — Matrix

## Objectif
Lire le fichier `.htsecret`. Le fichier source `index.php.txt` est disponible.

## Faille / Catégorie OWASP
**CWE-259: Use of Hard-coded Password**  
**CWE-327: Broken or Risky Crypto Algorithm**

## Démarche d'exploitation
1. Accès à `index.php.txt` (même technique que l'étape Icare)
2. Lecture du code source : processus d'authentification similaire à Icare, mot de passe haché en SHA-1
3. Récupération du hash SHA-1 du mot de passe depuis le code source
4. Déchiffrement via un outil en ligne → mot de passe : **`poney`**

SHA-1 est un algorithme de hachage cryptographiquement cassé, dont les hash courants sont indexés dans des bases de données publiques (*rainbow tables*).

## Recommandations
- Stocker le mot de passe dans une variable d'environnement au sein d'un fichier de configuration sécurisé, hors du code source
- Utiliser un algorithme de hachage moderne et adapté aux mots de passe : Argon2 ou Bcrypt (résistants aux attaques par force brute et rainbow tables)

## Certificat
`00882dfbdbcc2677d0a0a1cb99a054400feb0dc4266f621f5ec67b83f199524da711d4599bb11964`
