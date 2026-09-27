# Politique de confidentialité — Jeu de la Route

Texte source de [confidentialite.html](confidentialite.html) (page bilingue publiée).
Ce fichier sert de référence facile à relire ; c'est la page HTML qui doit être collée
dans la Play Console, pas ce fichier.

---

**Dernière mise à jour : 3 septembre 2026**

Le Jeu de la Route est une application développée par Olivier Popiers. Cette politique
explique quelles données l'application traite, pourquoi, et comment exercer vos droits.

## Ce que l'application collecte

### Données enregistrées sur votre appareil

Vos meilleurs scores (par catégorie, par mode et par format de réponse), vos compteurs
de réussite et d'échec par question, et vos réglages (sons, vibrations, thème) sont
enregistrés localement sur votre téléphone. Rien de tout cela n'est envoyé à un serveur :
le jeu fonctionne entièrement hors ligne. Si vous avez activé la sauvegarde automatique
d'Android, ce fichier peut être copié dans votre espace Google Drive personnel par le
système, sans que le développeur y ait accès.

Ces données sont supprimées lorsque vous désinstallez l'application. Vous pouvez aussi
les effacer à tout moment depuis **Réglages → Réinitialiser les scores**.

### Publicité

L'application affiche une publicité plein écran entre deux parties, via **Google AdMob**,
pour rester gratuite. AdMob peut accéder à l'**identifiant publicitaire** de votre
appareil pour mesurer l'audience et, si vous y consentez, personnaliser les annonces. Le
traitement effectué par Google est décrit dans sa propre politique :
https://policies.google.com/technologies/partner-sites

### Consentement

Si vous résidez dans l'Espace économique européen, au Royaume-Uni ou en Suisse, un
message de consentement (RGPD/TCF, via Google UMP) s'affiche au premier lancement, avant
toute publicité personnalisée. Vous pouvez revenir sur votre choix à tout moment depuis
**Réglages → Choix publicitaires**.

## Ce que l'application ne fait pas

- Aucun compte à créer, aucune adresse e-mail demandée.
- Aucun accès à votre position, vos contacts, votre appareil photo, votre micro, vos
  fichiers ou votre carnet d'adresses.
- Aucun classement en ligne, aucun pseudo, aucune interaction avec d'autres joueurs.
- Aucune donnée vendue à des tiers.
- Aucun achat en argent réel.
- Aucune question ne nécessite de connexion Internet ; seule la publicité en utilise une.

## Durée de conservation

Aucune donnée n'est conservée par le développeur : rien n'est envoyé à un serveur propre
à l'application. Seul Google (AdMob) peut conserver l'identifiant publicitaire selon sa
propre politique. Les données locales (scores, statistiques, réglages) restent sur votre
appareil jusqu'à la désinstallation, ou jusqu'à ce que vous les réinitialisiez depuis les
réglages.

## Vos droits

Pour toute question sur les données traitées par AdMob, voir la politique de Google liée
ci-dessus. Pour toute autre question, ou pour supprimer l'ensemble de vos données
locales, utilisez **Réglages → Réinitialiser les scores**, désinstallez l'application, ou
écrivez à l'adresse ci-dessous.

## Enfants

L'application ne s'adresse pas spécifiquement aux enfants et ne collecte pas sciemment de
données auprès d'eux.

## Modifications

Toute modification de cette politique sera publiée à cette même adresse, avec une date de
mise à jour actualisée.

## Contact

olivier3dprint@gmail.com

---

## Statut de publication

Ce fichier est le **brouillon source, en français uniquement**. La version à donner à
Play est la page HTML publiée [confidentialite.html](confidentialite.html) — bilingue
(FR par défaut, `?lang=en` force l'anglais), même principe que les autres projets : une
seule URL pour les deux langues, puisque Play n'accepte qu'un champ de politique de
confidentialité par application, pas par fiche linguistique.

Publiée sur `github.com/olivier3dprint/JeuDeLaRoute` (dépôt public dédié au site) via
GitHub Pages, et **en ligne** à
`https://olivier3dprint.github.io/JeuDeLaRoute/confidentialite.html` — vérifié le
3 septembre 2026, contenu identique au fichier de ce dossier. Procédure de republication
dans [fiche-play.md](fiche-play.md), section « Site — page d'accueil et politique de
confidentialité ».

> ⚠️ Cette URL est référencée à trois endroits : la console AdMob (message de consentement
> européen), la chaîne `url_confidentialite` de
> [strings.xml](../app/src/main/res/values/strings.xml) et, à terme, la fiche Play. Elle ne
> peut plus changer sans mettre les trois à jour ensemble.

Si le texte change (achat « Sans publicité », classement en ligne du backlog, nouvelle
donnée collectée…), modifier **deux fichiers** : celui-ci pour la trace en français, et
`confidentialite.html` — ils ne sont pas synchronisés automatiquement.

**Vérifier la cohérence avec le formulaire Sécurité des données** de la Play Console : ce
qui est déclaré là-bas doit correspondre à ce texte. Le tableau de référence est dans
[fiche-play.md](fiche-play.md).
