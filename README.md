# Régie mariage — synchro en temps réel

# Coordination soirée — synchro en temps réel

Une page HTML principale (`communication.html`), utilisée par les deux personnes (Julien et Freddy), synchronisée via Firebase Realtime Database :
- En haut : **Envoi** — mes boutons (Prépare-toi, GO, STOP, Pas Prêt, Prêt) + ma zone de texte
- En bas : **Reçu** — les voyants qui s'allument selon ce que l'autre a appuyé + le texte qu'il a envoyé

Au premier chargement, la page demande le code d'accès puis "Tu es qui ?" (Julien ou Freddy) et s'en souvient ensuite sur cet appareil (bouton "Changer" en haut pour réinitialiser si besoin).

Une seconde page (`sono.html`), accessible uniquement depuis la page de Freddy via le bouton "🎛️ Réglages sono", propose des boutons Volume +/- et Reverbe +/-. Chaque appui déclenche un popup sur la page de Julien.

## Mise en route (5 minutes)

1. Créer un projet sur https://console.firebase.google.com
2. Dans le projet, aller dans **Build > Realtime Database** > "Créer une base de données" > démarrer en **mode test**
3. Dans **Paramètres du projet > Général**, ajouter une application Web, copier la config
4. Coller cette config dans `firebase-config.js`
5. Mettre les 4 fichiers (`communication.html`, `communication.css`, `sono.html`, `firebase-config.js`) dans un repo GitHub public
6. Activer **GitHub Pages** dans les paramètres du repo (Settings > Pages > Source: branche main)
7. Ouvrir `communication.html` sur les deux téléphones, choisir son identité, tester

## Personnaliser

- Les couleurs sont dans `communication.css` : `.yellow`, `.green`, `.red` pour les boutons/voyants, fond alu brossé sombre
- Pour ajouter/retirer un état (ex: un 6ᵉ bouton), dupliquer un `<button class="action-btn ...">` dans `communication.html` et son équivalent `<div class="indicator ...">` dans la section Reçu, avec le même `data-val`
- Pour ajouter un bouton sur la page sono, dupliquer un `<button class="action-btn ...">` dans `sono.html` avec un nouveau `data-val` — le popup sur la page de Julien affichera automatiquement ce texte

## Sécuriser avant le jour J (optionnel mais recommandé)

Le mode test laisse la base ouverte à tout le monde. Pour restreindre un minimum,
dans Realtime Database > Règles, remplacer par :

```json
{
  "rules": {
    ".read": true,
    ".write": true
  }
}
```

Pour un usage aussi court (une soirée), le mode test suffit largement — la restreindre est une option, pas une obligation.

## Anciennes pages (régie/affichage à sens unique)

`regie.html`, `affichage.html` et leurs `.css` restent dans le repo si besoin, mais ne sont plus utilisés depuis le passage à la communication bidirectionnelle.

