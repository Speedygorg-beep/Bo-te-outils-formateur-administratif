# Outils enseignants

Boîte à outils numérique pour l'équipe enseignante : des pages qui génèrent des
documents administratifs prêts à copier ou à exporter (PDF / Word / texte).

## Principe

- Aucun compte, aucune connexion requise pour les enseignants qui utilisent les outils
- Aucun appel à une IA pendant l'utilisation → pas de coût récurrent
- Rien n'est envoyé à un serveur : tout se passe dans le navigateur
- Les données viennent soit d'un formulaire rempli sur place, soit d'un fichier
  importé et traité localement, soit de contenus de référence déjà intégrés à l'outil

## Outils disponibles

- **Mots aux familles** (`mots-aux-familles.html`) — absence, retard, comportement,
  encouragement, convocation, mot libre
- **Appréciations bulletin** (`appreciations-bulletin.html`) — appréciation composée
  à partir des résultats, de l'investissement et du comportement de l'apprenant
- **Assistant cahier de textes** (`assistant-cahier-textes.html`) — met en forme le
  contenu de séance et le travail à faire, prêt à coller dans Yparéo
- **Compte-rendu de visite en entreprise** (`compte-rendu-visite-entreprise.html`) — missions
  observées, bilan, points de vigilance et actions à mener en visite d'entreprise
- **Adaptateur de mise en page** (`adaptateur-mise-en-page.html`) — reprend un
  texte collé et adapte sa présentation (police, taille, espacements, fond de
  page, une phrase par ligne) pour les besoins dys/PAP, sans jamais modifier
  le texte lui-même
- **Grille de correction assistée** (`grille-correction-assistee.html`) —
  notez chaque critère d'une grille modifiable (respect de la consigne,
  structure, contenu, expression écrite, présentation…), la note est
  calculée et un commentaire de correction est rédigé automatiquement

## Utiliser ce site

Une fois GitHub Pages activé sur ce dépôt (Settings → Pages → Deploy from branch →
`main` / `root`), le site est accessible à `https://<compte>.github.io/<dépôt>/`.
`index.html` sert de page d'accueil et renvoie vers chaque outil.

## Mettre à jour ou ajouter un outil

Chaque outil est un fichier HTML autonome (CSS et JS inclus, aucune dépendance
externe hormis Google Fonts). Pour ajouter un outil : déposer le nouveau fichier
`.html` dans ce dépôt et ajouter une carte correspondante dans `index.html`. Pour
corriger un outil existant : remplacer le fichier du même nom.

Tout outil doit inclure, en haut de sa page (dans la barre `.topbar`, juste
au-dessus du titre `.brand`), un lien de retour vers l'accueil, pour que
l'enseignant puisse toujours revenir choisir un autre outil :

```html
<a class="back-link" href="index.html">← Boîte à outils</a>
```

avec le style correspondant (déjà présent dans les outils existants, à copier
tel quel dans le nouveau fichier) :

```css
.back-link{
  display:inline-flex; align-items:center; gap:6px;
  font-family:'IBM Plex Sans', sans-serif; font-weight:600; font-size:0.88rem;
  color:var(--accent); text-decoration:none;
  background:var(--accent-soft); border:1px solid var(--accent);
  padding:7px 16px; border-radius:999px;
  margin-bottom:12px;
  transition: background .15s ease, color .15s ease;
}
.back-link:hover{ background:var(--accent); color:var(--accent-ink); }
.back-link:focus-visible{ outline:2px solid var(--accent); outline-offset:3px; }
```

(nécessite que la page définisse aussi `--accent-ink`, déjà présent dans les
outils existants — copier ces variables si le nouvel outil part d'une palette
différente.)

Tout outil doit aussi donner un retour visuel après clic sur le bouton
« Générer » : le formulaire étant souvent plus long que la zone de résultat,
rien ne garantit que le résultat soit visible sans cela. Convention à copier
depuis un outil existant : donner `id="outputPanel"` à la `<section
class="panel">` qui contient la zone de résultat, puis appeler
`scrollToOutput()` (fonction utilitaire déjà présente dans chaque outil, à
copier telle quelle) à la toute fin de la fonction `showLetter()` /
`showEntry()` / `showReport()` (celle qui affiche le texte généré) — elle
fait défiler la page jusqu'au résultat et l'entoure d'un bref halo (classe
CSS `.just-generated` + `@keyframes panelFlash`, également à copier).
