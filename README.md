# LaTeX DevContainer - Articles en Français

Environnement de développement LaTeX configuré pour la rédaction d'articles scientifiques en français avec gestion de bibliographie.

## 🚀 Démarrage rapide

### Prérequis
- [VS Code](https://code.visualstudio.com/)
- [Docker Desktop](https://www.docker.com/products/docker-desktop/)
- Extension VS Code : [Dev Containers](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-containers)

### Installation
1. Copiez ce dossier dans votre projet
2. Ouvrez le projet dans VS Code
3. `F1` → **Dev Containers: Reopen in Container**
4. Attendez la construction de l'image (~5-10 min la première fois)

## 📁 Structure du projet

```
projet/
├── .devcontainer/
│   ├── devcontainer.json   # Configuration VS Code
│   └── Dockerfile          # Image Docker
├── article.tex             # Template d'article
├── references.bib          # Bibliographie
├── .gitignore
└── README.md
```

## ✨ Fonctionnalités incluses

### Extensions VS Code
- **LaTeX Workshop** : compilation, preview, synctex
- **LTeX** : correcteur orthographique français
- **Code Spell Checker French** : dictionnaire français

### Paquets LaTeX
| Catégorie | Paquets |
|-----------|---------|
| Français | babel-french, csquotes |
| Bibliographie | biblatex, biber |
| Mise en page | geometry, fancyhdr, titlesec |
| Tableaux | booktabs, multirow |
| Maths | amsmath, siunitx |
| Liens | hyperref, cleveref |

## 🔧 Utilisation

### Compilation
- **Automatique** : sauvegardez le fichier (Ctrl+S)
- **Manuelle** : `Ctrl+Alt+B` ou clic sur ▶️

### Recettes de compilation
1. `latexmk (lualatex)` - Recommandé, support Unicode complet
2. `latexmk (pdflatex)` - Plus rapide, compatibilité maximale
3. `pdflatex → biber → pdflatex×2` - Compilation manuelle

### Commandes utiles
| Action | Raccourci |
|--------|-----------|
| Compiler | `Ctrl+Alt+B` |
| Voir PDF | `Ctrl+Alt+V` |
| Synctex (tex→pdf) | `Ctrl+Alt+J` |
| Nettoyer fichiers | `Ctrl+Alt+C` |

## 📚 Bibliographie

Le fichier `references.bib` contient des exemples pour :
- `@article` - Article de revue
- `@book` - Livre
- `@inproceedings` - Conférence
- `@online` - Site web
- `@thesis` - Thèse

### Citation dans le texte
```latex
\cite{exemple2023}           % [1]
\textcite{exemple2023}       % Dupont et Martin [1]
\parencite{exemple2023}      % (Dupont et Martin, 2023)
```

## 🎨 Personnalisation

### Changer le style de bibliographie
Dans `article.tex`, modifier la ligne :
```latex
style=numeric,    % → authoryear, apa, ieee, etc.
```

### Utiliser LuaLaTeX avec polices système
Décommenter dans `article.tex` :
```latex
\usepackage{fontspec}
\setmainfont{TeX Gyre Termes}
```

## ❓ Dépannage

| Problème | Solution |
|----------|----------|
| Bibliographie vide | Vérifier que biber s'exécute (voir Output → LaTeX Workshop) |
| Accents mal affichés | Utiliser LuaLaTeX au lieu de pdfLaTeX |
| Image première compilation | Patience, ~5-10 min pour télécharger |

## 📄 Licence

Ce template est libre d'utilisation.
