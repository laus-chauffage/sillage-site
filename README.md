# sillage.aero — le site

Pages **statiques** : aucun serveur, aucune base, aucun formulaire. Publiées
par GitHub Pages sur le domaine `sillage.aero` (fichier `CNAME`).

## Ce que c'est

Quatre pages par langue (accueil, questions fréquentes, conditions,
confidentialité), plus les captures de l'app et le logo. Le bouton « Rejoindre
l'essai » mène au lien public TestFlight.

## Comment ça s'est fabriqué

Le site a d'abord été une application Next.js (dépôt `sillage`, privé) servie
par un conteneur Scaleway. Le 12/10/2026 il est devenu statique : le HTML a été
pris tel qu'il était servi, puis nettoyé (scripts retirés, formulaire remplacé,
pages légales réécrites) par `scripts/generer-site-statique.py` du dépôt
`sillage`.

⚠️ Ce script ne peut plus tourner : sa source — l'application en ligne —
n'existe plus. **Le HTML de ce dépôt est désormais la source.** Il se modifie à
la main ; un commit sur `main` suffit à publier.

## Les pièges, si vous y touchez

- `CNAME` porte le domaine : le supprimer casse l'adresse.
- `.nojekyll` évite que GitHub Pages ignore des fichiers.
- Les quatre pages de chaque langue se répondent par des liens absolus
  (`/fr/faq`, `/en/faq`…) et par `hreflang` : si vous renommez un dossier,
  reprenez aussi les `<link rel="canonical">` et `sitemap.xml`.
- `assets/site.css` est la feuille compilée par Tailwind. Elle ne se régénère
  plus : on édite les classes existantes, on n'en invente pas.
