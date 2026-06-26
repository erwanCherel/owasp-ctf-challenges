# SQWeb — Sécurité des applications web

Module de sécurité web (Bachelor – TIC-SEC3) consistant en une série de challenges d'exploitation de failles, dans un environnement légal dédié.

## Objectifs

- Acquérir les automatismes de programmation sécurisée
- Exploiter les différentes failles de sécurité des applications web
- Formuler des recommandations concrètes pour les corriger

## Étapes résolues

| # | Nom | Faille / Catégorie OWASP | Fichier |
|---|-----|--------------------------|---------|
| 01 | Javapass | A07:2021 – Identification and Authentication Failures | [etape-01-javapass.md](etape-01-javapass.md) |
| 02 | Calc | A03:2021 – Injection (`eval()`) | [etape-02-calc.md](etape-02-calc.md) |
| 03 | Hacker vaillant | A04:2021 – Insecure Design / CWE-434: Unrestricted File Upload | [etape-03-hacker-vaillant.md](etape-03-hacker-vaillant.md) |
| 04 | Medium Invaders | Cross-Site Request Forgery (CSRF) | [etape-04-medium-invaders.md](etape-04-medium-invaders.md) |
| 05 | Flipper | A01:2021 – Broken Access Control (Cookie Tampering) | [etape-05-flipper.md](etape-05-flipper.md) |
| 06 | Calc v2 | A03:2021 – Injection (backticks) | [etape-06-calc-v2.md](etape-06-calc-v2.md) |
| 07 | Calc v6 | A03:2021 – Injection (`phpinfo()`) | [etape-07-calc-v6.md](etape-07-calc-v6.md) |
| 08 | Icare | A01:2021 – Broken Access Control (parameter injection) | [etape-08-icare.md](etape-08-icare.md) |
| 09 | Ma petite boutique | Cookie Manipulation (sérialisation PHP) | [etape-09-ma-petite-boutique.md](etape-09-ma-petite-boutique.md) |
| 10 | Ushuaia | Code Injection (`.htaccess` + `AddType`) | [etape-10-ushuaia.md](etape-10-ushuaia.md) |
| 11 | Matrix | CWE-259: Hard-coded Password / CWE-327: Broken Crypto (SHA-1) | [etape-11-matrix.md](etape-11-matrix.md) |
| 12 | Ushuaia v2 | Code Injection (`.htaccess` + `AddType`) | [etape-12-ushuaia-v2.md](etape-12-ushuaia-v2.md) |
| 13 | XaSSebook_1 | CWE-79: Cross-Site Scripting (XSS) | [etape-13-xassebook-1.md](etape-13-xassebook-1.md) |
| 14 | XaSSebook_3 | CWE-79: Cross-Site Scripting (XSS) | [etape-14-xassebook-3.md](etape-14-xassebook-3.md) |
| 15 | XaSSebook_5 | CWE-79: Cross-Site Scripting (XSS – attribute injection) | [etape-15-xassebook-5.md](etape-15-xassebook-5.md) |

## Failles couvertes

- **Injection** : PHP `eval()`, backticks, `phpinfo()`, upload + `.htaccess`
- **Broken Access Control** : cookie tampering, parameter injection
- **XSS** : reflected XSS, attribute injection
- **CSRF** : replay d'un formulaire sans token
- **Mauvaise gestion des fichiers uploadés** : extension non vérifiée, `.htaccess` non désactivé
- **Cryptographie faible** : SHA-1, mot de passe en dur dans le code source
- **Cookie non sécurisé** : données non signées, non chiffrées, non validées côté serveur
