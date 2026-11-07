# Portfolio — Maintenance intelligente & Stratégies 4.0

Site statique (HTML, CSS, JavaScript, sans compilation). Le contenu s'écrit en Markdown : personne n'a besoin de toucher au code.

## Structure

```
index.html              page du site (ne pas modifier sauf évolution du design)
contenu/
  sommaire.json         ordre et titres des sections du menu
  00-accueil.md …       une page Markdown par section
projets/
  projets.json          les 4 emplacements de projets (PRJ-01 à PRJ-04)
  GUIDE-AJOUT.md        procédure pour ajouter un projet prêt
  projet-1/index.md     fiche du projet pompe (binôme du coordinateur)
  projet-2/             emplacement libre
  projet-3/             emplacement libre
  projet-4/             emplacement libre (projet individuel)
src/app.html            source de la page (copie utilisée pour l'aperçu en ligne)
```

## Ouvrir le site en local

Le site charge ses pages par `fetch`, il ne s'ouvre donc pas par double-clic sur `index.html`.

- **VS Code** : installer l'extension *Live Server*, clic droit sur `index.html` → *Open with Live Server*.
- **Python** : dans le dossier du site, `python -m http.server`, puis ouvrir `http://localhost:8000`.

## Rédiger une section

1. Ouvrir le fichier de la section dans `contenu/` (par exemple `04-lean.md`).
2. Remplacer les listes « Points exigés » et « À traiter aussi » par le texte rédigé.
3. Mettre à jour la ligne d'état en haut : `> **État :** rédigé · **Responsable :** Nom`.
4. Les tableaux Markdown, les liens et les images (`![légende](contenu/img/figure.png)`) sont pris en charge.

## Ajouter un projet prêt

Voir `projets/GUIDE-AJOUT.md`, ou ouvrir la page d'un emplacement libre sur le site : elle contient un formulaire qui génère la fiche à coller dans `projets/projets.json`.

## Publier sur GitHub Pages

1. Créer un dépôt GitHub et y pousser le contenu de ce dossier.
2. *Settings → Pages → Build and deployment* : source *Deploy from a branch*, branche `main`, dossier `/ (root)`.
3. Le site est disponible à l'adresse indiquée par GitHub quelques minutes plus tard. C'est ce lien qu'on remet au professeur.

## Dépendances externes

- Rendu Markdown : `marked` 12.0.2 chargé depuis jsDelivr. Sans connexion, le texte s'affiche brut.
- Polices Google Fonts (Barlow Condensed, IBM Plex Sans, IBM Plex Mono), avec polices système de secours.
