# vital-brief-content

Contenu quotidien de l'app **[Vital Brief](https://github.com/pierreespy/vital-brief)** —
veille infirmière (onglets Journal + Mot du jour).

L'app télécharge **`edition.json`** à chaque lancement / pull-to-refresh, via GitHub
Pages :

```
https://pierreespy.github.io/vital-brief-content/edition.json
```

## Fichiers

- **`edition.json`** — l'édition du jour affichée par l'app. Format défini par le type
  `Edition` (voir `src/content/types.ts` dans le dépôt app). C'est ce fichier qu'on
  remplace chaque matin.
- **`recent-words.json`** — mémoire des « mots du jour » récents (anti-répétition). Sert à
  la **génération**, pas à l'app.
- **`.nojekyll`** — désactive le traitement Jekyll (GitHub Pages sert les fichiers tels
  quels).

## Chaque matin

1. Choisir le mot du jour + rédiger le Journal (1 actu par rubrique) en suivant
   `daily-content/GENERATION.md` du dépôt app.
2. Écrire le nouvel **`edition.json`** ici.
3. Mettre à jour **`recent-words.json`** (ajouter le terme du jour en tête, tronquer à ~30).
4. `git commit` + `git push` → l'app récupère l'édition au prochain lancement.

> **Robustesse** : si ce fichier est indisponible, l'app retombe sur la dernière édition
> en cache, puis sur l'édition d'exemple intégrée. Jamais d'écran vide.

## Activer GitHub Pages (une fois)

Settings → Pages → **Build and deployment** → Source : *Deploy from a branch*, Branch :
`main` / `/ (root)`. L'URL ci-dessus devient alors active.
