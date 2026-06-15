# Template de rapport PFE EHTP

![PAGE DE GARDE](page.png)

## Version actuelle

Cette version du template compile un seul chapitre numéroté : `Chapters/Chapter1.tex`. Ce chapitre contient des exemples d'utilisation pour les figures, tableaux, équations, code Python coloré, boîtes colorées, listes et références internes.

## Structure

```text
.
├── main.tex
├── Variables.tex
├── TitlePage.tex
├── MainLayout/
│   ├── ConfigPackages.tex
│   ├── Fonts.tex
│   ├── PageLayout.tex
│   ├── ChapterStyle_1.tex
│   └── ReportSettings.tex
├── FrontMatter/
├── Chapters/
├── BackMatter/
├── assets/fonts/amiri/
└── .github/workflows/latex.yml
```

## Fichiers importants

- `main.tex` : fichier principal, ordre des pages et inclusion des chapitres.
- `Variables.tex` : titre, nom, encadrants, année, logos et fond de page.
- `TitlePage.tex` : structure visuelle de la page de garde.
- `MainLayout/ConfigPackages.tex` : packages, couleurs globales, boîtes colorées, listes, code coloré et couleurs des liens.
- `MainLayout/Fonts.tex` : langues et polices, notamment le français et l'arabe.
- `MainLayout/PageLayout.tex` : marges, interligne, paragraphes, entêtes et numérotation.
- `MainLayout/ChapterStyle_1.tex` : style graphique des titres de chapitres.
- `MainLayout/ReportSettings.tex` : légendes, références figure/tableau/code, boîtes colorées, style des blocs de code, mini-sommaire et fond de page.
- `Chapters/Chapter1.tex` : chapitre d'exemples d'utilisation.

## Personnalisation rapide

Modifie les informations principales dans `Variables.tex`:

```tex
\newcommand{\ReportTitle}{Titre du projet}
\newcommand{\StudentName}{Prénom NOM}
\newcommand{\SupervisorOne}{Pr. Nom Prénom (Organisme)}
\newcommand{\SupervisorTwo}{Pr. Nom Prénom (EHTP)}
\newcommand{\AcademicYear}{2025/2026}
```

Les images utilisées par défaut sont à la racine du projet :

- `ehtp.png`
- `images.png`
- `MEE2.png`
- `DGM.png`
- `arriere2.png`

Pour remplacer une image, garde le même nom de fichier ou change le nom dans `Variables.tex`:

```tex
\newcommand{\LogoLeft}{ehtp.png}
\newcommand{\CoverBackground}{arriere2.png}
```

## Guide de mise en page

### 1. Changer les couleurs principales

Les couleurs globales sont définies dans `MainLayout/ConfigPackages.tex` :

```tex
\definecolor{bleuLille1}{RGB}{22,150,255}
\definecolor{darkgray}{RGB}{70,70,70}
```

La couleur `bleuLille1` est utilisée pour :

- les titres de chapitres ;
- le carré de numéro de chapitre ;
- les labels des figures et tableaux ;
- les références internes `\figref` et `\tabref` ;
- les liens de citation et URL.

Exemples de couleurs:

```tex
\definecolor{bleuLille1}{RGB}{0,102,204}   % bleu institutionnel
\definecolor{bleuLille1}{RGB}{0,120,90}    % vert
\definecolor{bleuLille1}{RGB}{160,40,40}   % rouge sombre
```

### 2. Changer la couleur des liens

Toujours dans `MainLayout/ConfigPackages.tex`, les liens PDF sont configurés ici :

```tex
\usepackage[
  colorlinks=true,
  linktoc=all,
  linkcolor=darkgray,
  citecolor=bleuLille1,
  urlcolor=bleuLille1
]{hyperref}
```

Paramètres utiles :

- `linkcolor` : couleur des liens internes, table des matières, figures, tableaux.
- `citecolor` : couleur des citations bibliographiques.
- `urlcolor` : couleur des liens web.
- `colorlinks=true` : affiche les liens en couleur au lieu d'un cadre.

### 3. Changer les marges

Les marges sont dans `MainLayout/PageLayout.tex`:

```tex
\geometry{
  a4paper,
  left=2.5cm,
  right=2.5cm,
  top=2.8cm,
  bottom=2.8cm,
  headheight=21pt
}
```

Paramètres importants:

- `left` et `right` : marges gauche et droite.
- `top` et `bottom` : marges haute et basse.
- `headheight` : hauteur réservée à l'entête.
- `a4paper` : format de page.

Exemple pour un rapport plus aéré:

```tex
left=3cm,
right=3cm,
top=3cm,
bottom=3cm,
```

### 4. Changer l'interligne et les paragraphes

Dans `MainLayout/PageLayout.tex`:

```tex
\OnehalfSpacing
\setlength{\parindent}{1.2em}
\setlength{\parskip}{0.2em}
```

Paramètres utiles :

- `\OnehalfSpacing` : interligne 1,5.
- `\SingleSpacing` : interligne simple.
- `\DoubleSpacing` : double interligne.
- `\parindent` : retrait au début des paragraphes.
- `\parskip` : espace vertical entre paragraphes.

### 5. Changer les entêtes et numéros de page

Les entêtes sont dans `MainLayout/PageLayout.tex`:

```tex
\makepagestyle{pfe}
\makeoddhead{pfe}{\leftmark}{}{\thepage}
\makeevenhead{pfe}{\thepage}{}{\leftmark}
\makeheadrule{pfe}{\textwidth}{0.4pt}
\pagestyle{pfe}
```

Signification:

- `\leftmark` : affiche le titre courant du chapitre.
- `\thepage` : affiche le numéro de page.
- `0.4pt` : épaisseur de la ligne d'entête.

Pour enlever la ligne d'entête:

```tex
\makeheadrule{pfe}{\textwidth}{0pt}
```

Pour afficher seulement le numéro de page à droite:

```tex
\makeoddhead{pfe}{}{}{\thepage}
\makeevenhead{pfe}{}{}{\thepage}
```

### 6. Changer le style des chapitres

Le style des chapitres est dans `MainLayout/ChapterStyle_1.tex`.

Couleur du carré contenant le numéro:

```tex
\colorbox{bleuLille1!80!black}{...}
```

Couleur du numéro dans le carré:

```tex
\centering\color{white}\bfseries\sffamily\scriptsize\thechapter
```

Couleur et taille du titre de chapitre:

```tex
\renewcommand\chaptitlefont{\normalfont\huge\bfseries\color{bleuLille1!80!black}}
```

Paramètres utiles :

- `\huge` : taille du titre. Alternatives: `\Large`, `\LARGE`, `\Huge`.
- `\bfseries` : texte en gras.
- `\color{...}` : couleur du titre.
- `\raggedleft` : alignement à droite.

Pour centrer les titres de chapitres:

```tex
\renewcommand\printchaptertitle[1]{\chaptitlefont\centering ##1\par}
```

Pour changer la hauteur du marqueur de chapitre:

```tex
\feline@chm[0.35cm]
```

Augmente `0.35cm` pour un numéro plus grand.

### 7. Changer les labels de figures et tableaux

Les labels de légendes sont dans `MainLayout/ReportSettings.tex` :

```tex
\captionnamefont{\normalfont\small\bfseries\color{bleuLille1!80!black}}
\captiontitlefont{\normalfont\small\itshape}
\captiondelim{ : }
```

Paramètres utiles :

- `\captionnamefont` : style de `Figure 1` ou `Table 1`.
- `\captiontitlefont` : style du texte de la légende.
- `\captiondelim` : séparateur entre label et texte.

Exemples :

```tex
\captionnamefont{\normalfont\small\bfseries\color{red}}
\captiontitlefont{\normalfont\small}
\captiondelim{ -- }
```

Les noms affichés sont aussi définis dans `ReportSettings.tex` :

```tex
\renewcommand{\figurename}{Figure}
\renewcommand{\tablename}{Table}
```

Tu peux les remplacer par:

```tex
\renewcommand{\figurename}{Fig.}
\renewcommand{\tablename}{Tab.}
```

### 8. Changer la couleur des références figure/tableau

Toujours dans `MainLayout/ReportSettings.tex`:

```tex
\newcommand{\figref}[1]{\textcolor{bleuLille1}{\hyperref[#1]{\textit{Figure~\ref*{#1}}}}}
\newcommand{\tabref}[1]{\textcolor{bleuLille1}{\hyperref[#1]{\textit{Table~\ref*{#1}}}}}
```

Pour utiliser une autre couleur, change `bleuLille1` :

```tex
\textcolor{darkgray}{...}
```

### 9. Insérer une remarque ou un point clé coloré

Les boîtes colorées sont définies dans `MainLayout/ReportSettings.tex` avec le package `tcolorbox`, chargé dans `MainLayout/ConfigPackages.tex`.

Pour insérer une remarque :

```tex
\begin{remarkbox}[Remarque]
Texte de la remarque.
\end{remarkbox}
```

Pour insérer un point important :

```tex
\begin{keybox}[Point clé]
Texte important à retenir.
\end{keybox}
```

Paramètres de couleur disponibles dans `ReportSettings.tex`:

```tex
\definecolor{remarkbackground}{RGB}{240,248,255}
\definecolor{remarkframe}{RGB}{22,150,255}
\definecolor{keybackground}{RGB}{255,248,225}
\definecolor{keyframe}{RGB}{210,140,20}
```

Signification:

- `remarkbackground` : couleur de fond de la boîte remarque.
- `remarkframe` : couleur du cadre et du titre de la boîte remarque.
- `keybackground` : couleur de fond de la boîte point clé.
- `keyframe` : couleur du cadre et du titre de la boîte point clé.

Pour changer le titre affiché dans la boîte, modifie le texte entre crochets:

```tex
\begin{remarkbox}[Hypothèse]
Cette hypothèse sera utilisée dans la suite du chapitre.
\end{remarkbox}
```

### 10. Utiliser les différents types de listes

Le template charge `enumitem`, ce qui permet d'utiliser des listes simples, numérotées, descriptives et personnalisées.

Liste simple avec `itemize` :

```tex
\begin{itemize}
  \item premier élément ;
  \item deuxième élément ;
  \item troisième élément.
\end{itemize}
```

Liste numérotée avec `enumerate` :

```tex
\begin{enumerate}
  \item Collecter les données.
  \item Nettoyer les fichiers.
  \item Interpréter les résultats.
\end{enumerate}
```

Liste descriptive avec `description` :

```tex
\begin{description}
  \item[Objectif] Expliquer le but du travail.
  \item[Méthode] Présenter la démarche utilisée.
  \item[Résultat] Résumer les principaux enseignements.
\end{description}
```

Liste avec puce colorée personnalisée :

```tex
\begin{itemize}[label=\textcolor{bleuLille1}{$\blacktriangleright$}]
  \item idée importante ;
  \item autre idée importante.
\end{itemize}
```

Liste avec tirets :

```tex
\begin{itemize}[label=--]
  \item élément court ;
  \item autre élément court.
\end{itemize}
```

Pour changer la couleur des puces personnalisées, remplace `bleuLille1` par une autre couleur définie avec `\definecolor`.

### 11. Changer le mini-sommaire de chapitre

Chaque chapitre peut afficher un mini-sommaire avec:

```tex
\chaptertoc
```

La commande est définie dans `MainLayout/ReportSettings.tex` :

```tex
\newcommand{\chaptertoc}{%
  \startcontents[chapters]%
  \noindent{\large\bfseries Sommaire}\par
  \noindent\hrulefill\par
  \printcontents[chapters]{l}{1}{\setcounter{tocdepth}{2}}%
}
```

Paramètres utiles :

- `Sommaire` : titre affiché dans le chapitre.
- `tocdepth` : profondeur affichée.
- `1` dans `\printcontents` : niveau de départ.

Pour ne pas afficher de mini-sommaire, supprime `\chaptertoc` dans le fichier du chapitre.

### 12. Changer la page de garde

La page de garde est dans `TitlePage.tex`. Les logos sont affichés ici :

```tex
\TemplateImage[width=0.9\textwidth]{\LogoLeft}
\TemplateImage[width=\textwidth]{\LogoCenter}
\TemplateImage[width=\textwidth]{\LogoRight}
```

Pour changer la taille d'un logo, modifie `width`:

```tex
\TemplateImage[width=0.7\textwidth]{\LogoLeft}
```

Les lignes horizontales sont ici :

```tex
\noindent\rule{\linewidth}{0.4pt}
```

- `\linewidth` : largeur de la ligne.
- `0.4pt` : épaisseur de la ligne.

Le fond de page est géré dans `MainLayout/ReportSettings.tex`:

```tex
\ThisCenterWallPaper{1.0}{#1}
```

- `1.0` : taille normale.
- `1.2` : image agrandie.
- `0.8` : image réduite.

### 13. Changer les polices et langues

Les polices sont dans `MainLayout/Fonts.tex`.

Langues :

```tex
\setmainlanguage{french}
\setotherlanguage{arabic}
```

Police principale :

```tex
\setmainfont{Latin Modern Roman}
```

Police arabe locale :

```tex
\newfontfamily\arabicfont[
  Script=Arabic,
  Scale=1.1,
  Path=./assets/fonts/amiri/,
  Extension=.ttf,
  UprightFont=*-Regular,
  BoldFont=*-Bold,
  ItalicFont=*-Italic,
  BoldItalicFont=*-BoldItalic
]{Amiri}
```

Paramètre utile:

- `Scale=1.1` : taille relative de la police arabe.

### 14. Ajouter ou retirer des chapitres

Dans `main.tex`, le corps du rapport contient actuellement un seul chapitre:

```tex
\input{Chapters/Chapter1}
```

Pour ajouter un deuxième chapitre :

```tex
\input{Chapters/Chapter2}
```

Pour retirer un chapitre, supprime ou commente sa ligne :

```tex
% \input{Chapters/Chapter2}
```

### 15. Tables des matières, figures et tableaux

Les sommaires principaux sont dans `FrontMatter/Listes.tex`:

```tex
\tableofcontents
\listoffigures
\listoftables
```

La profondeur du sommaire est dans `MainLayout/ReportSettings.tex`:

```tex
\setcounter{tocdepth}{2}
\setcounter{secnumdepth}{3}
```

- `tocdepth=1` : chapitres et sections.
- `tocdepth=2` : chapitres, sections et sous-sections.
- `secnumdepth=3` : numérotation jusqu'aux sous-sous-sections.

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

## GitHub Actions

À chaque `push` ou `pull request`, GitHub Actions compile `main.tex` et publie `main.pdf` comme artefact téléchargeable.

## Publication sur GitHub

```powershell
git init
git add .
git commit -m "Initial GitHub-ready LaTeX template"
git branch -M main
git remote add origin https://github.com/USER/REPO.git
git push -u origin main
```

Remplace `USER` et `REPO` par ton compte GitHub et le nom du dépôt.
