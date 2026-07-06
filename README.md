# Générateur de signatures électroniques — GAFA Pay

Page web statique qui génère des signatures email HTML pour les collègues de GAFA Pay :
nom / prénom, rôle, email, téléphone, entreprise, site web, avec le logo GAFA
intégré (embarqué en base64, s'affiche partout, y compris sur mobile et hors ligne).

## Utilisation

1. Ouvrir la page (en local : ouvrir `index.html` dans un navigateur ; en ligne : l'URL Vercel).
2. Remplir les champs du collègue. L'aperçu se met à jour en temps réel.
3. Choisir un **style de signature** parmi 4 templates : Classique, Compact, Moderne, Bandeau.
4. Exporter au format voulu :
   - **« Copier la signature »** (HTML riche) puis coller dans la config de signature :
     - **Gmail** : Paramètres → Voir tous les paramètres → Signature → Ctrl/Cmd+V
     - **Outlook** : Fichier → Options → Courrier → Signatures
     - **Apple Mail** : Réglages → Signatures
   - **« Copier le code HTML »** pour les outils qui demandent le code source.
   - **« Télécharger .html »** pour archiver un fichier par personne.

## Templates disponibles

- **Classique** — logo à gauche, barre verticale verte, infos à droite.
- **Compact** — mise en page sur une ligne, minimaliste (idéal mobile).
- **Moderne** — logo en haut, bloc aéré avec accent de marque.
- **Bandeau** — bloc à fond vert GAFA, texte blanc, plus visuel.

Tous les templates restent en mise en page `<table>` pour la compatibilité clients mail.

## Détails techniques

- 100 % statique : un seul fichier `index.html`, aucune dépendance, aucun build.
- Le logo GAFA est embarqué en base64 dans le HTML → aucune dépendance réseau,
  s'affiche même quand le client mail bloque les images externes.
- Couleur de marque : vert GAFA `#3F8A49` (extrait du logo officiel).
- Interface modernisée : cartes, ombres douces, aperçu en direct, sélecteur de templates.
- Exports multi-format : copie HTML riche (`ClipboardItem` avec repli `execCommand`),
  copie du code source (`writeText`), et téléchargement `.html` autonome.
- Mise en page en `<table>` pour la compatibilité avec les clients mail.

## Déploiement (Vercel)

Le projet est statique — Vercel le sert tel quel, aucune configuration de build.
Connecter le repo GitHub sur [vercel.com](https://vercel.com/new) : chaque push
sur la branche principale redéploie automatiquement.

## Structure

```
index.html          La page + générateur (logo embarqué à l'intérieur)
assets/logo_gafa.png Logo source (référence, non utilisé au runtime)
vercel.json         Config Vercel (site statique)
```
