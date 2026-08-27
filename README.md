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
  display:inline-block; font-family:'IBM Plex Mono', monospace; font-size:0.72rem;
  color:var(--accent); text-decoration:none; letter-spacing:0.02em; margin-bottom:6px;
}
.back-link:hover{ text-decoration:underline; }
.back-link:focus-visible{ outline:2px solid var(--accent); outline-offset:2px; border-radius:3px; }
```
