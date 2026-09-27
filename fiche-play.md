# Fiche Google Play — Jeu de la Route

Textes à copier-coller dans la console Play. Les limites de caractères indiquées sont
celles imposées par Play ; le décompte réel de chaque texte est donné à côté — à
revérifier si le texte est modifié.

✅ **Application publiée sur Google Play** :
<https://play.google.com/store/apps/details?id=com.olivier.jeudelaroute>
(`applicationId = "com.olivier.jeudelaroute"`). Version en ligne vérifiée le
27 septembre 2026 : `versionName = "2026.09.07.2"` (`versionCode = 4` dans
[app/build.gradle.kts](../app/build.gradle.kts)) — le prochain envoi devra donc porter un
`versionCode` ≥ 5. Nom et description courte affichés sur Play identiques aux textes
ci-dessous : les modifier ici **puis** dans la console, sinon cette fiche cesse d'être la
référence.

Contenu toujours conforme à [jeu-de-la-route-spec.md](../jeu-de-la-route-spec.md) :
5 catégories (27 + 50 + 101 + 27 + 50 = 255 entrées dans
[assets/data/](../app/src/main/assets/data)), 3 modes, 2 formats de réponse, scores et
statistiques locaux, interstitiel AdMob de fin de partie.

> **Historique de publication** — les deux premiers envois ont été refusés par Google
> pour un plantage au démarrage, invisible en debug : deux suppressions silencieuses par
> R8 (sérialiseurs kotlinx.serialization, puis constructeur de `WorkDatabase_Impl` tiré
> par AdMob via WorkManager). Correctifs commentés dans
> [app/proguard-rules.pro](../app/proguard-rules.pro). Avant tout nouvel envoi :
> **tester le build release signé sur un vrai téléphone**, pas seulement vérifier que
> `bundleRelease` réussit.

**Fiche en français uniquement.** Contrairement à PhotoCalc, l'application n'est pas
traduite : son interface et surtout son contenu sont français (« Maine-et-Loire »,
« Tchéquie », les 101 départements). Une fiche anglaise attirerait un public qui ne peut
pas jouer — mauvaises notes garanties. À rouvrir le jour où l'app est réellement
traduite. Les textes anglais des pages du site (`index.html`, `confidentialite.html`)
sont, eux, bien présents : Play n'accepte **qu'une seule** URL de politique de
confidentialité pour toutes les langues, elle doit donc être lisible par un relecteur
non francophone.

---

## Nom de l'application

*(30 caractères max — 15 utilisés)*

```
Jeu de la Route
```

## Description courte

*(80 caractères max — 70 utilisés)*

```
Codes, départements, capitales : le quiz de géo qui se joue en voiture
```

## Description complète

*(4000 caractères max — environ 1580 utilisés)*

```
Le Jeu de la Route transforme les plaques d'immatriculation et les panneaux en quiz : combien de codes pays et de départements savez-vous vraiment lire ? Une seule erreur et la partie s'arrête — votre score, c'est la longueur de votre série.

■ CINQ CATÉGORIES
Codes des 27 pays de l'Union européenne, codes de l'Europe géographique (une cinquantaine de pays), 101 départements français, capitales de l'UE et capitales de l'Europe. Environ 255 entrées, toutes gratuites.

■ TROIS MODES DE JEU
Série : une erreur et c'est fini, le score est votre meilleure série.
Contre-la-montre : 60 secondes pour enchaîner un maximum de bonnes réponses, chaque erreur coûte 3 secondes.
Entraînement : sans score et sans fin, pour apprendre tranquillement.

■ DEUX FAÇONS DE RÉPONDRE
QCM : quatre propositions, jouable d'une seule main.
Révélation : la question s'affiche seule, vous répondez de tête ou à voix haute, puis vous découvrez la solution et vous vous auto-évaluez. Parfait pour jouer à plusieurs autour d'un seul téléphone.

■ PENSÉ POUR LA VOITURE
Gros boutons, texte lisible, thème sombre par défaut pour la conduite de nuit, mode portrait à une main, retour haptique à chaque réponse.

■ VOS PROGRÈS
Meilleur score par catégorie, par mode et par format de réponse. Taux de réussite et classement des entrées les plus ratées, pour savoir quoi réviser.

■ 100 % HORS LIGNE
Aucun compte, aucune inscription, aucune donnée envoyée à un serveur. Tout fonctionne sans connexion — essentiel sur la route. Une publicité occasionnelle, entre deux parties, finance l'application gratuite.
```

---

## Classification et catégorie

| Champ | Valeur |
|---|---|
| Type | **Jeu** (pas une application — le questionnaire IARC et les catégories en dépendent) |
| Catégorie | Quiz (*Trivia*) |
| Tags | Quiz, Éducatif, Géographie, Culture générale |
| Public cible | Tout public |
| Contient des annonces | **Oui** (interstitiel AdMob de fin de partie) |
| Achats via l'application | **Non** — l'achat « Sans publicité » de la section 11 de la spec est au backlog, aucun code de facturation n'est présent aujourd'hui |

## Questionnaire de classification du contenu (IARC)

Aucun contenu sensible : pas de violence, contenu sexuel, langage grossier, drogues,
jeux d'argent. **Pas d'interaction entre utilisateurs** : pas de compte, pas de
classement en ligne, pas de pseudo visible des autres joueurs — le classement en ligne
est explicitement hors périmètre V1 (section 9 de la spec). Le bouton « Partager » de
l'écran Résultat ouvre le sélecteur Android avec un texte pré-rempli : c'est un partage
sortant vers l'app choisie par le joueur, pas une fonctionnalité sociale interne.
Pas de partage de position ni de coordonnées personnelles.

> ⚠️ À revoir **le jour où le classement en ligne du backlog est implémenté** : un pseudo
> visible des autres joueurs fait passer la réponse à « les utilisateurs peuvent-ils
> interagir entre eux ? » de non à **oui**. Répondre non par réflexe est un motif
> classique de rejet.

## Sécurité des données

À déclarer, sans quoi la fiche est rejetée :

| Donnée | Collectée | Partagée | Pourquoi |
|---|---|---|---|
| Identifiant publicitaire | Oui | Oui | Publicité (SDK AdMob) |

Aucune autre donnée n'est collectée : pas de compte, pas de position, pas de contacts,
pas de fichiers. Les meilleurs scores, les statistiques par entrée et les réglages
restent stockés localement (`SharedPreferences`, voir
[PrefsStore.kt](../app/src/main/java/com/olivier/jeudelaroute/data/PrefsStore.kt)) et ne
sont jamais envoyés à un serveur. Le SDK AdMob ajoute lui-même la permission
`com.google.android.gms.permission.AD_ID` au manifeste : Play rejette une application qui
la déclare sans déclarer l'usage correspondant ci-dessus.

Données chiffrées en transit ? **Oui** (AdMob en HTTPS). Le jeu lui-même ne fait aucun
appel réseau : les 5 fichiers de questions sont embarqués dans l'APK
([assets/data/](../app/src/main/assets/data)).

### Version anglaise — pour référence uniquement

⚠️ **Le formulaire Sécurité des données n'est pas traduisible dans la Play Console** :
c'est une déclaration unique par application, Google affiche automatiquement les libellés
dans la langue du visiteur.

| Data | Collected | Shared | Why |
|---|---|---|---|
| Advertising ID | Yes | Yes | Advertising (AdMob SDK) |

Data encrypted in transit? **Yes** (AdMob over HTTPS). Scores, per-entry statistics and
settings stay on device and are never uploaded.

## Identifiants AdMob

Déjà en place dans le code (pas des identifiants de test) — créés le 3 septembre 2026 :

| Élément | Valeur |
|---|---|
| ID d'application (manifeste) | `ca-app-pub-7930855717646694~6913142649` |
| Bloc « Interstitiel fin de partie » | `ca-app-pub-7930855717646694/1517240535` |
| Bloc de test (builds debug) | `ca-app-pub-3940256099942544/1033173712` |

La bascule test/production est **automatique** selon `BuildConfig.DEBUG`
([IdsAdMob.kt](../app/src/main/java/com/olivier/jeudelaroute/ads/IdsAdMob.kt)) : un build
de debug sert le bloc de test, un build release (l'AAB envoyé à Play) sert le bloc réel —
rien à changer à la main avant l'envoi. Le consentement RGPD/TCF (Google UMP) est géré
par [ConsentementPublicitaire.kt](../app/src/main/java/com/olivier/jeudelaroute/ads/ConsentementPublicitaire.kt),
avec un point d'entrée « Choix publicitaires » dans Réglages
([ReglagesScreen.kt](../app/src/main/java/com/olivier/jeudelaroute/ui/reglages/ReglagesScreen.kt)).

L'application est rattachée au message de consentement européen du compte AdMob
(6 applications), avec l'URL de confidentialité ci-dessous, et **le message est publié**
— vérifié dans la console le 3 septembre 2026.

> ☐ **À vérifier dans AdMob maintenant que la fiche existe** : l'application doit être liée à sa fiche
> Play (Applications → Paramètres de l'application → *Plate-formes de téléchargement*).
> Tant que ce n'est pas fait, elle reste en état *Examen requis* et les annonces servies
> sont limitées.

## Visuels

Générés par [visuels/generer_visuels.py](visuels/generer_visuels.py) à partir des
illustrations sources du projet — détails et méthode dans
[visuels/NOTES.md](visuels/NOTES.md).

| Fichier | Format | Usage |
|---|---|---|
| `icone_512.png` | 512×512 PNG | Icône de la fiche Play (obligatoire) — l'illustration source réduite, pas une capture agrandie |
| `fr/banniere_1024x500.png` | 1024×500 PNG | Image mise en avant |
| `fr/capture-*.png` | 1080×2400 PNG | Captures d'écran du téléphone (2 minimum exigées par Play, 8 maximum) |

## Site — page d'accueil et politique de confidentialité

Même principe que PhotoCalc et Calculatrice H/M : un **dépôt public dédié au site**,
distinct du dépôt de code, parce que GitHub Pages sur dépôt privé exige un plan payant et
que la politique de confidentialité doit être lisible sans authentification.

`index.html` et `confidentialite.html` vivent **à la racine** du dépôt du site (pas dans
un sous-dossier : en mode `main` / `/ (root)`, GitHub Pages ne sert `index.html` qu'à la
racine).

| Fichier | Rôle | URL | État |
|---|---|---|---|
| `index.html` | Page d'accueil, bilingue | `https://olivier3dprint.github.io/JeuDeLaRoute/` | **modifiée localement le 27/09/2026, à republier** |
| `confidentialite.html` | Politique de confidentialité, bilingue (FR par défaut, `?lang=en` force l'anglais) | `.../confidentialite.html` | **en ligne** (HTTP 200) |

Vérifié le 27 septembre 2026 : les deux pages en ligne étaient **strictement identiques**
aux fichiers de ce dossier (comparaison octet par octet) avant la modification de
`index.html` décrite plus bas. `confidentialite.html` n'a pas changé. Les fichiers d'ici
restent la source ; toute correction se fait ici puis se repousse sur le dépôt du site.

> ⚠️ **Le dépôt public s'appelle `JeuDeLaRoute`**, et cette URL est saisie à trois
> endroits : la console AdMob (message de consentement européen), la chaîne
> `url_confidentialite` de [strings.xml](../app/src/main/res/values/strings.xml) — lue par
> le bouton « Règles de confidentialité » des Réglages — et la fiche Play. Renommer
> le dépôt casse les trois d'un coup. Le code source, lui, vit dans un dépôt distinct,
> `olivier3dprint/JeuDeLaRouteSources`.

Le bandeau inactif « BIENTÔT SUR GOOGLE PLAY » de la page d'accueil a été remplacé le
27 septembre 2026 par un vrai bouton « DISPONIBLE SUR GOOGLE PLAY » / « GET IT ON GOOGLE
PLAY » pointant vers la fiche (classe `bouton-play` dans `index.html`). **Cette version
n'est pas encore en ligne** : la republier avec les commandes ci-dessous.

**Pour republier après une modification** (commandes à lancer dans ton propre terminal —
aucune authentification GitHub ne passe par Claude) :

```bash
git clone https://github.com/olivier3dprint/JeuDeLaRoute.git jeu-de-la-route-site
```

```bash
copy "D:\dev\Jeu de la route\playstore\index.html" jeu-de-la-route-site\index.html
```

```bash
copy "D:\dev\Jeu de la route\playstore\confidentialite.html" jeu-de-la-route-site\confidentialite.html
```

```bash
cd jeu-de-la-route-site && git add index.html confidentialite.html && git commit -m "Met a jour la page d'accueil et la politique de confidentialite" && git push
```

Pour contrôler que la mise en ligne a bien pris (doit répondre `200`) :

```bash
curl -s -o /dev/null -w "%{http_code}\n" https://olivier3dprint.github.io/JeuDeLaRoute/confidentialite.html
```

## Champs de la console Play (renseignés)

⚠️ **La politique de confidentialité n'est PAS un champ par langue** dans la Play Console
(Surveiller et améliorer → Règles et programmes → Contenu de l'application → Règles de
confidentialité) — un seul champ pour toute l'application, d'où la page bilingue unique
`confidentialite.html`.

| Champ | Valeur |
|---|---|
| Politique de confidentialité | `https://olivier3dprint.github.io/JeuDeLaRoute/confidentialite.html` |
| Site web (facultatif — présence à vérifier dans la console) | `https://olivier3dprint.github.io/JeuDeLaRoute/` |
| Adresse e-mail de contact | `olivier3dprint@gmail.com` |

Rappels pour les prochains envois :

- **Pays et régions** — configurés **par piste**. Une piste sans pays rend l'application
  introuvable, y compris pour les testeurs internes, avec un message « Élément
  introuvable » trompeur dans le Play Store.
- **Keystore de release** — `keystore.properties` est en place (hors dépôt, voir
  `.gitignore`) et signe les builds release. Le keystore lui-même doit rester sauvegardé
  **hors du dépôt** : le perdre interdit toute mise à jour future de l'application.
- **`versionCode` strictement croissant** — Play refuse un numéro déjà utilisé, même en
  test interne (dernier envoyé : 4).
- **Test interne d'abord** : aucune revue Google, disponible en minutes. Ensuite
  **promouvoir** la release plutôt que la re-téléverser, pour publier exactement le
  binaire testé.
