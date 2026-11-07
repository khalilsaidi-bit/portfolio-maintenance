# Ajouter un projet prêt dans un emplacement libre

Les emplacements PRJ-02 et PRJ-03 sont libres. Pour y placer un projet terminé :

1. **Déposer les fichiers** dans le dossier de l'emplacement, par exemple `projets/projet-2/` :
   - `index.md` : la fiche du projet (optionnel mais recommandé) ;
   - les fichiers à joindre : rapport PDF, diapositives, images, archive du code.
2. **Remplir la fiche** dans `projets/projets.json` : remplacer le bloc de l'emplacement par celui que génère le formulaire « Préparer la fiche » de la page de l'emplacement libre (bouton Copier), puis passer `"libre"` à `false`.
3. **Vérifier en local** : lancer `python -m http.server` à la racine du site, ou l'extension Live Server de VS Code, et ouvrir la page du projet.

## Champs de la fiche

| Champ | Obligatoire | Exemple |
|---|---|---|
| `titre` | oui | Analyse de fiabilité d'un parc de compresseurs |
| `equipe` | oui | `["Nom 1", "Nom 2"]` |
| `resume` | oui | Deux ou trois phrases |
| `statut` | oui | `termine`, `en_cours` ou `a_venir` |
| `sous_titre`, `equipement`, `tache`, `donnees` | non | Texte libre |
| `outils`, `mots_cles` | non | Listes de textes |
| `page` | non | `projets/projet-2/index.md` |
| `lien_projet` | non | Adresse d'un projet déjà publié ailleurs (site, dépôt GitHub) |
| `liens` | non | `[{ "label": "Dépôt GitHub", "url": "https://…" }]` |
| `fichiers` | non | `[{ "label": "Rapport (PDF)", "chemin": "projets/projet-2/rapport.pdf" }]` |
