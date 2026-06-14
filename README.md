# Template de rapport PFE EHTP

Template LaTeX pour un rapport de Projet de Fin d'Etude EHTP. Le projet est pret pour GitHub: les sources sont versionnables, les fichiers temporaires LaTeX sont ignores, et un workflow GitHub Actions peut compiler le PDF automatiquement.

## Structure

```text
.
├── main.tex
├── Variables.tex
├── TitlePage.tex
├── MainLayout/
├── FrontMatter/
├── Chapters/
├── BackMatter/
├── assets/fonts/amiri/
└── .github/workflows/latex.yml
```

## Personnalisation

Modifie les informations principales dans `Variables.tex`:

- titre du rapport
- nom de l'etudiant
- encadrants
- organisme d'accueil
- annee academique
- logos et fond de page

Les images utilisees par defaut sont a la racine du projet:

- `ehtp.png`
- `images.png`
- `MEE2.png`
- `DGM.png`
- `arriere2.png`

## Compilation locale

Le projet utilise LuaLaTeX pour supporter `fontspec`, `polyglossia` et le texte arabe.

```powershell
lualatex -interaction=nonstopmode main.tex
lualatex -interaction=nonstopmode main.tex
```

Avec `latexmk`:

```powershell
latexmk main.tex
```

