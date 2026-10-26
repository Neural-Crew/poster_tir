@.claude/CLAUDE-commun.md

# CLAUDE.md — poster_tir

Poster scientifique (TIR) sur l'état de l'art des Small Language Models, en LaTeX (gabarit beamerposter « gemini »). Dépôt partagé avec : Eliot, Titouan, Henrei, Damien.
Config du socle : `_dev/projet.json`. Règles communes : `.claude/CLAUDE-commun.md` (ne pas dupliquer ici).

## Stack

- LaTeX beamer + beamerposter, thème `beamerthemegemini.sty` / `beamercolorthememsu.sty`, bibliographie BibTeX `references_finales.bib`.
- Moteur : **xelatex** (imposé par `.latexmkrc` : `$pdf_mode = 5`, `$pdflatex = 'xelatex %O %S'`), compilé à l'origine sous MiKTeX.
- Générés (ne pas éditer) : `poster.pdf`, `poster.aux`, `.bbl`, `.blg`, `.fdb_latexmk`, `.log`, `.nav`, `.out`, `.snm`, `.toc` (tous versionnés).

## Commandes

```bash
node {outils}/verifier-tout.js   # cf. commandes.verifier
latexmk poster.tex               # build (xelatex via .latexmkrc) — commandes.construire laissé null : xelatex absent sur ce PC
```

## Gros risques du projet

En plus de `CLAUDE-commun.md` § 3 :
- ⛔ Ne pas éditer ni supprimer `references_finales.bib` : c'est la seule bibliographie lue par `poster.tex`.
- ⛔ Ne pas commiter `poster.pdf` et les fichiers de build sans avoir recompilé avec xelatex.

## Pièges

- Installe `texlive-xetex` avant de compiler : sans xelatex, `latexmk -pdf` sort en 12 (« xelatex: not found »), et forcer pdflatex échoue (le source vise XeTeX).
- Compile dans une copie ou restaure les fichiers de build après coup : ils sont versionnés, une compilation locale salit `git status`.
- Ne confonds pas `references_finales.bib` (utilisé) avec `references_finales (1).bib` et `poster.bib` (non référencés par `poster.tex`).
- Il n'y a ni INT, ni VAL, ni PROD : seule `main` (branche par défaut) et la branche `Eliot` existent sur origin.
