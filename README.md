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
