# Audit d'Arène Maths (octobre 2026)

Bilan complet du jeu : pédagogie, banque de questions, figures, design, technique. Chaque point indique ce qui a été constaté, ce qui a été corrigé, et ce qui reste à faire.

## Synthèse

| Domaine | Constat | État |
|---|---|---|
| Jauges | 43 questions de calcul déguisées en curseur, 4 angles à estimer « à l'œil », valeur affichée pendant le glissement | Corrigé |
| Répétition | 20 à 35 questions fixes par chapitre : les mêmes reviennent après 2 ou 3 parties | Corrigé (146 modèles générés) |
| Vrai / faux | 139 « vrai » pour 72 « faux » : répondre « Vrai » au hasard rapporte trop | Atténué |
| Distracteurs | 10 QCM où la bonne réponse se repère à sa longueur | Corrigé |
| Typographie | « 6ème », « 5ème »… au lieu de « 6e », « 5e » | Corrigé |
| Figures | 306 figures vérifiées automatiquement ; titre d'axe coupé sur les diagrammes en barres | Corrigé |
| Exactitude | 1 573 questions fixes et 146 modèles vérifiés par programme | Aucune erreur trouvée |

## 1. Pédagogie

### Les jauges
**Constat.** Sur 69 questions à jauge, seules 26 travaillaient vraiment la droite graduée. Les autres étaient des calculs (moyenne, distance, aire, Thalès…) où le curseur ralentissait la réponse sans rien apporter. Les quatre questions « Estime la mesure de l'angle AÔB » demandaient une précision de 5° à l'œil nu, ce qui n'est ni juste ni conforme au programme. Enfin, le curseur affichait la valeur en grand pendant le glissement : « placer 3 » revenait à faire défiler jusqu'à lire 3, sans aucune compétence de repérage.

**Corrections.**
- 39 questions de calcul passent en « réponse à taper », avec un énoncé reformulé quand il parlait de jauge.
- Les 4 questions d'angle deviennent des QCM : nature de l'angle (aigu, droit, obtus, plat) ou ordre de grandeur avec des propositions bien séparées (45°, 90°, 135°, 10°). Le distracteur 50° pour un angle de 130° reprend l'erreur classique de lecture du rapporteur.
- La jauge devient une vraie **droite graduée** : un trait par graduation, des nombres seulement sur les repères (entiers, multiples de 5 pour les relatifs, 0,5 sur une droite de 0 à 1). L'élève fait glisser ou touche un point, sans voir la valeur avant de valider : il doit compter les graduations. Utilisable au clavier (flèches).
- Les graduations sont adaptées à la notion : quarts pour placer 3/4, demis pour placer 2,5, dixièmes pour 0,3.
- La jauge est désormais réservée aux questions où le repérage est la compétence visée : fractions, décimaux, relatifs, échelle des probabilités, encadrement d'une racine carrée, cosinus entre 0 et 1.

### La variété des questions
**Constat.** Chaque chapitre comptait 20 à 35 questions fixes. Une classe qui joue chaque semaine voit les mêmes énoncés revenir rapidement et finit par mémoriser les réponses.

**Correction : 146 modèles de questions générées**, au moins un par chapitre (deux ou trois pour la plupart). À chaque partie, les valeurs sont tirées au hasard, la bonne réponse est calculée par le programme et l'explication est rédigée avec les vraies valeurs. Les distracteurs reprennent les erreurs typiques :
- additionner les dénominateurs (fractions) ;
- calculer (a + b) × c au lieu de a + b × c (priorités) ;
- oublier le ÷ 2 de l'aire du triangle, le 1/3 du cône, le r² du cylindre ;
- additionner des pourcentages successifs ;
- écrire 2,5 h « 2 h 50 » ;
- confondre image et antécédent, côté adjacent et côté opposé ;
- confondre longueurs, aires et volumes dans un agrandissement…

Environ un tiers des questions d'une partie sont générées. Dans « Vérifier les questions », chaque modèle s'affiche avec un exemple, un bouton « Autre exemple » et un interrupteur pour le désactiver.

**Contrôle.** Chaque modèle a été tiré 400 fois par un script. Le script vérifie :
- 4 propositions distinctes, y compris en valeur (1/2 et 2/4 ne peuvent pas coexister) ;
- aucun nombre au format anglais ;
- des réponses à taper courtes et exactes ;
- des points de droite graduée situés sur une graduation ;
- l'équilibre des vrai/faux, entre 35 % et 65 % de « vrai ».

Plus de 700 exemples ont ensuite été relus à la main.

### Autres corrections
- 10 QCM où la bonne réponse était nettement plus longue que les autres : distracteurs réécrits à longueur comparable.
- Niveaux écrits « 6e », « 5e », « 4e », « 3e » (« 6ème » est une faute de typographie).

## 2. Figures et graphismes
- 306 figures (questions fixes et exemples générés) rendues dans le navigateur. Un script a contrôlé que chaque étiquette reste dans le cadre et ne chevauche pas une autre.
- Seul défaut trouvé : le titre « Effectif » des diagrammes en barres sortait du cadre. Corrigé.
- Les questions de Pythagore générées affichent un triangle rectangle avec les longueurs connues et un « ? » sur la longueur cherchée. Celles de Thalès affichent la figure emboîtée ou papillon avec les données en légende.

## 3. Design et ergonomie
- Accueil : un mode d'emploi en trois étapes (choisir, ouvrir la salle, scanner) et un pied de page qui indique qu'aucune donnée personnelle n'est conservée.
- Compteurs : nombre de questions fixes et de modèles par chapitre.
- Détecteur de design Impeccable : aucun signalement.
- Vérifié à 1 280 px et sur téléphone (375 px), sans défilement horizontal.

## 4. Technique
- Une partie complète de 25 questions jouée automatiquement pour chaque niveau : tous les types (QCM, vrai/faux, droite graduée, réponse à taper, ordre, rédaction), questions fixes et générées, mode Boss jusqu'au K.O. Aucune erreur JavaScript, toutes les bonnes réponses acceptées.
- Connexion des téléphones par Supabase (région Paris), testée en conditions réelles ; PeerJS reste en secours.

## 5. Ce qui reste à faire avant de vendre
Ces points ne relèvent pas du code ou demandent une décision de votre part.

1. **Relecture par un enseignant.** Les vérifications automatiques garantissent l'exactitude des calculs, pas l'adéquation fine au programme de chaque niveau. En particulier, le programme de 5e entre en vigueur en 2026 : comparez les intitulés des chapitres au texte officiel.
2. **Contrôle d'accès et licences.** Le code est public sur GitHub : n'importe qui peut copier le jeu. Pour vendre, il faut un dépôt privé, un hébergement maîtrisé et un accès par compte enseignant ou par code d'établissement. Supabase peut stocker les licences.
3. **Documents légaux.** Il faut des mentions légales, des conditions générales de vente et une politique de confidentialité. Pour les établissements, ajoutez un document qui décrit les traitements de données, même minimaux : pseudos et réponses transitent par Supabase (hébergé en Europe) sans être stockés.
4. **Test en classe réelle** avec 25 à 30 téléphones sur le Wi-Fi du collège, pour mesurer la tenue de la connexion.
5. **Accessibilité.** Le jeu respecte les bases (contraste, clavier, réduction des animations), mais un audit RGAA complet est conseillé pour répondre aux marchés publics.
6. **Explications.** 485 explications font moins de 25 caractères (par exemple « 9/12 + 10/12 = 19/12. »). Elles sont justes mais pourraient être enrichies progressivement d'une phrase de méthode.
7. **Vrai / faux de la banque fixe.** Le déséquilibre initial (139 vrais, 72 faux) est compensé en partie par les modèles générés, équilibrés. Réécrire une quarantaine d'affirmations vraies en fausses rééquilibrerait complètement la banque.
