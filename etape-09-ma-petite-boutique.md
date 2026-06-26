# Étape 09 — Ma petite boutique

## Objectif
Parvenir à un total à payer négatif.

## Faille / Catégorie OWASP
**Cookie Manipulation**

## Démarche d'exploitation
1. Inspection de la console → cookie nommé `panier` contenant une valeur URL-encodée :
   ```
   a%3A3%3A%7Bi%3A1%3Bi%3A0%3Bi%3A2%3Bi%3A0%3Bi%3A3%3Bi%3A0%3B%7D
   ```
   Décodée : `a:3:{i:1;i:0;i:2;i:0;i:3;i:0;}` (sérialisation PHP)

2. En modifiant le panier, on comprend que chaque produit est associé à une valeur modifiable directement dans le cookie

3. Utilisation d'un outil d'encodage/décodage en ligne pour modifier la valeur d'un produit à `-10` :
   ```
   a:3:{i:1;i:-10;i:2;i:0;i:3;i:0;}
   ```

4. Validation du panier → total négatif → certificat affiché

## Recommandations
- Signer le contenu du cookie avec un algorithme HMAC et une clé secrète
- Chiffrer les données du cookie avec un algorithme comme AES
- Vérifier les données côté serveur pour s'assurer de leur cohérence (quantités positives, produits existants)

## Certificat
`12ef6c8aafc78bcd4719930c2a8049f6f164df98a2b8d03276ae217a1b94b97348a57c2e44940d4b`
