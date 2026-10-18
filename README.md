# Arène Maths

Le quiz de maths en direct pour le collège, de la 6e à la 3e. Les questions s'affichent au tableau, les élèves répondent sur leur téléphone (ou en équipes sur ardoise), et la séance se termine par un podium et un bilan pour le professeur.

## Ce que contient le jeu

- **1 573 questions** réparties en 61 chapitres (6e, 5e, 4e, 3e), avec une explication pour chaque réponse.
- **6 mécaniques** : QCM, vrai ou faux, jauge à placer, réponse à taper, remettre dans l'ordre, rédaction de démonstration à glisser.
- **Figures** générées : transformations, Thalès (imbriqué et papillon), trigonométrie, graphiques de fonctions, diagrammes, arbres de probabilités.
- **3 modes** : téléphones (QR code + code à 6 chiffres), équipes (le professeur coche les équipes qui ont trouvé), solo.
- **Mode Boss** : toute la classe affronte un monstre (Fractodon, Hypoténus, Aléatorix ou Bugzilla selon les chapitres). Chaque bonne réponse lui retire des points de vie ; il faut environ 60 % de réussite pour le mettre K.O.
- **Distinctions de fin** : Sans faute, Coup fatal, Éclair, Inarrêtable, Remontada, Cerveau, Œil de lynx. Elles s'affichent au podium et sur le téléphone de chaque élève.
- **Réactions** : les élèves envoient 🔥 👏 😮 😂 💪 🤯 depuis leur téléphone ; elles s'envolent sur l'écran projeté (pas pendant les questions).
- **Montée en tension** : musique dont le tempo accélère avec le chrono, vignette rouge et battements de cœur dans les 5 dernières secondes, annonce de la dernière question, écarts serrés commentés au classement.
- **Bilan de séance** : réussite par notion, par élève et par question, copie ou export CSV (Excel).
- **Vérifier les questions** : le professeur peut consulter et désactiver chaque question.

Tout tient dans un seul fichier `index.html`, sans installation ni compte.

## Mettre en ligne avec GitHub Pages

1. Créez un dépôt sur GitHub et déposez `index.html` à la racine.
2. Dans le dépôt : **Settings → Pages → Build and deployment**, choisissez **Deploy from a branch**, branche `main`, dossier `/ (root)`.
3. Après une minute, le jeu est disponible à l'adresse `https://<votre-compte>.github.io/<nom-du-depot>/`.

Le mode téléphones a besoin d'une adresse `https://` : il ne fonctionne pas en ouvrant le fichier depuis l'ordinateur. Les modes Équipes et Solo fonctionnent partout.

## Avant de le vendre

Ces points ne bloquent pas un usage en classe, mais ils comptent pour un produit payant.

1. **Serveur de connexion.** Sans configuration, les téléphones passent par le service public gratuit de PeerJS, sans garantie de disponibilité. Pour un produit vendu, activez Supabase (section suivante) : c'est gratuit pour démarrer et ça fonctionne sur les réseaux d'établissement.
2. **Code visible.** Une page GitHub Pages publique est lisible et copiable par tous. Pour vendre des licences, gardez le dépôt privé et publiez le jeu sur un hébergement que vous contrôlez (avec un accès par compte ou par code d'établissement).
3. **Licence.** Le fichier `LICENSE` réserve tous les droits. Complétez-y votre nom.
4. **Données personnelles (RGPD).** Le jeu ne crée aucun compte et n'envoie aucune donnée à un serveur applicatif : les élèves choisissent un pseudo, et seules les préférences (chapitres cochés, son, pseudo) restent dans le navigateur. C'est un argument pour les établissements ; gardez-le vrai si vous ajoutez des comptes.
5. **Programmes.** Les chapitres suivent les programmes de cycle 3 et 4. Relisez les intitulés de programme affichés sur l'accueil (notamment 5e 2026) au moment de la publication.

## Activer la connexion Supabase (gratuit)

Avec Supabase, le tableau et les téléphones communiquent par une connexion web sécurisée classique, que les réseaux d'établissement laissent presque toujours passer. Le tableau regroupe ses messages : une question ou une correction part en un seul envoi pour toute la classe.

1. Créez un compte gratuit sur [supabase.com](https://supabase.com) (avec GitHub ou une adresse e-mail).
2. Cliquez sur **New project** : nom `arene-maths`, un mot de passe de base de données (le jeu ne s'en sert pas, notez-le quand même), région **Europe** (Paris ou Francfort), offre **Free**.
3. Une fois le projet prêt, ouvrez **Project Settings → API Keys** et copiez :
   - l'**URL du projet** (de la forme `https://xxxxxxxx.supabase.co`, aussi visible avec le bouton **Connect**) ;
   - la **clé publique** : la *Publishable key* (`sb_publishable_…`) ou, dans l'onglet *Legacy API keys*, la clé `anon` `public`.
   N'utilisez jamais la clé *secret* ou `service_role` : elle donne tous les droits sur le projet.
4. Dans **Realtime → Settings**, vérifiez que l'accès public aux canaux est autorisé (réglage par défaut).
5. Ouvrez `index.html`, cherchez `NET_CFG` et collez les deux valeurs :
   ```js
   const NET_CFG={supabaseUrl:'https://xxxxxxxx.supabase.co',supabaseKey:'sb_publishable_…'};
   ```
6. Mettez le fichier en ligne, ouvrez la salle sur l'ordinateur et rejoignez-la avec un téléphone en données mobiles pour vérifier.

La clé publique est faite pour être visible dans une page web : elle ne permet ici que d'échanger des messages de jeu.

**Limites de l'offre gratuite** (à vérifier sur la page des tarifs de Supabase) : environ 200 connexions simultanées, soit 5 à 6 classes qui jouent en même temps, et un quota mensuel de messages qui couvre largement une centaine de séances. Un projet gratuit se met en pause après une semaine sans aucune utilisation : il se relance d'un clic depuis le tableau de bord. Pour un produit vendu à plusieurs établissements, passez à l'offre payante quand les ventes le permettent ; rien n'est à changer dans le jeu.

## Commandes utiles en classe

- `Espace` ou `Entrée` : révéler la réponse, puis passer à la suite.
- `F` : plein écran.
- En solo : touches `1` à `4` pour répondre aux QCM.
- Boutons **Son** et **Musique** dans la barre du haut pendant les questions.
