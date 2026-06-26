# Étape 05 — Flipper

## Objectif
Réussir à passer admin.

## Faille / Catégorie OWASP
**A01:2021 – Broken Access Control > Tampering cookie**

## Démarche d'exploitation
1. Tentative de connexion avec les identifiants `admin` / `admin`
2. Analyse de la requête via l'onglet *Network* des DevTools
3. L'onglet *Cookies* révèle une variable `admin` avec la valeur `0`
4. Modification de la valeur via la console JavaScript :
```js
document.cookie = 'admin=1'
```
5. Reconnexion → apparition du certificat

## Recommandations
- Chiffrer les données des cookies pour les rendre difficiles à lire et modifier
- Vérifier la valeur du cookie côté serveur (ne jamais faire confiance aux données client)

## Certificat
`0d9fbeef957914837e9572f8879cb7819dce559c3e3de5db555119f536a45c7446847f30e7adb2eb`
