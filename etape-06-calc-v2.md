# Étape 06 — Calc v2

## Objectif
Lire le fichier `.htsecret`.

## Faille / Catégorie OWASP
**A03:2021 – Injection**

## Démarche d'exploitation
Le site est une version légèrement corrigée de Calc. Tests successifs :

1. Réutilisation du code de l'étape 02 (`file_get_contents('.htsecret')`) → `SECURITY ERROR`
2. Opération arithmétique simple (`1+1`) → retourne un résultat : l'eval fonctionne encore
3. Opération sous forme de string (`"1+1"`) → `SECURITY ERROR` : les strings sont filtrées
4. Opération avec single quotes → `SECURITY ERROR`
5. **Backticks** → pas d'erreur : l'injection shell via backticks en PHP n'est pas filtrée

Exploitation avec backticks :
```
`ls -la`
```
Résultat : présence du fichier `.htsecret` dans le répertoire.

Lecture du fichier :
```
`cat .htsecret`
```

## Recommandations
- Étendre l'expression régulière pour couvrir les backticks et autres vecteurs d'injection shell
- Éviter l'utilisation de `eval()`
- Utiliser une librairie PHP dédiée aux opérations arithmétiques (ex. MathPHP)
- Modifier les droits de lecture de `.htsecret` avec `chmod`

## Certificat
`e55e70343a3f908381aec8c02e4a065cf688bff2461b61bfde3e4668e3c7b146024d42abff413cea`
