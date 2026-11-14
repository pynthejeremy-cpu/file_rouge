# Fil Rouge — site + back-office

## Les fichiers

| Fichier | Rôle |
|---|---|
| `index.html` | Le site. Ouverture animée au scroll, catalogue par catégorie, lecteur Vimeo. |
| `admin.html` | Le back-office. Édition des catégories, sous-catégories et films. |
| `data.json` | **Tout le contenu du site.** C'est le seul fichier à remplacer quand vous publiez. |
| `logo-fil-rouge-blanc.svg` / `-rouge.svg` | Le logo. |
| `.htaccess` | Exemple de protection du back-office (Apache / OVH / o2switch). |

## Mettre en ligne

Déposez les fichiers à la racine de votre hébergement (FTP, cPanel, Netlify, Vercel…).
Le site a besoin d'être servi par un serveur web : en double-cliquant `index.html` depuis
le bureau, le navigateur bloque la lecture de `data.json` (le site bascule alors sur la
copie de secours intégrée, qui ne tient pas compte de vos modifications).

## Le cycle de travail

1. Ouvrez `votresite.com/admin.html` — code d'accès : **filrouge**.
2. Modifiez : titres, clients, années, liens Vimeo, ordre, catégories, sous-catégories.
   - Collez l'URL Vimeo complète, l'identifiant est extrait automatiquement.
   - Le bouton **⤓** récupère le titre du film depuis Vimeo.
   - **▲ ▼** réordonnent, **✕** supprime.
3. **Aperçu sur le site** : vos modifications s'affichent immédiatement sur la page
   d'accueil, dans ce navigateur uniquement. Rien n'est encore public.
4. **Télécharger data.json**, puis remplacez `data.json` sur l'hébergement. C'est publié.
5. Si vous voulez repartir de la version en ligne : **Repartir du fichier en ligne**.

## Protéger le back-office

Le code d'accès dans `admin.html` empêche l'ouverture par curiosité, rien de plus :
le fichier reste lisible par qui connaît son adresse. Pour une vraie protection,
verrouillez-le côté serveur. Le `.htaccess` fourni fait ça sur un hébergement Apache —
il faut générer un fichier `.htpasswd` (votre hébergeur a un outil pour ça dans son panel).

Pour changer le code : dans `admin.html`, ligne `var CODE = "filrouge";`.
Mettre `""` désactive la demande de code.

## Le contenu

Catégories et sous-catégories reprennent exactement votre arborescence :

1. Accompagnement agence 360
2. Social content — *Reel campagne · Reel produit · Influence*
3. TV & web ads
4. Film corporate — *Films · Testimoniaux*
5. Brand movie
6. Film campagne
7. Film produit
8. Motion design
9. VFX
10. Live & VOG — *vide, à remplir*
11. Création sonore — *Voix off · Radio ads · Podcast — vides, à remplir*

74 films ont été repris du compte Vimeo **M LA CREATIVE** et répartis dans ces
rubriques. Certains films que vous citiez n'existent pas sur ce compte
(Georgette snake, Simons, reel tennis, reel golf, Jacadi Noël, Promod Afrique du Sud,
BZB denim, Pharmabest voir grand, Decathlon subsidiarité) : ajoutez-les depuis le
back-office avec leur lien Vimeo.

## Détails techniques

- Les vignettes viennent de l'API publique oEmbed de Vimeo et sont mises en cache
  dans le navigateur du visiteur. Aucune clé d'API, aucun compte à configurer.
- Le showreel d'ouverture est le film défini dans **Showreel** du back-office,
  lu en fond, muet, en boucle.
- Aucune dépendance, aucun build, aucun serveur applicatif : du HTML, du CSS et du
  JavaScript. Ça tiendra dans le temps.
