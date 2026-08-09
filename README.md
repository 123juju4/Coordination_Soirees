# Régie mariage — synchro en temps réel

# Coordination soirée — synchro en temps réel

Une seule page HTML (`communication.html`), utilisée par les deux personnes (Julien et Papa), synchronisée via Firebase Realtime Database :
- En haut : **Envoi** — mes boutons (Prépare-toi, GO, STOP, Pas Prêt, Prêt) + ma zone de texte
- En bas : **Reçu** — les voyants qui s'allument selon ce que l'autre a appuyé + le texte qu'il a envoyé

Au premier chargement, la page demande "Tu es qui ?" (Julien ou Papa) et s'en souvient ensuite sur cet appareil (bouton "Changer" en haut pour réinitialiser si besoin, par exemple si vous partagez le même téléphone).

## Mise en route (5 minutes)

1. Créer un projet sur https://console.firebase.google.com
2. Dans le projet, aller dans **Build > Realtime Database** > "Créer une base de données" > démarrer en **mode test**
3. Dans **Paramètres du projet > Général**, ajouter une application Web, copier la config
4. Coller cette config dans `firebase-config.js`
5. Mettre les 3 fichiers (`communication.html`, `communication.css`, `firebase-config.js`) dans un repo GitHub public
6. Activer **GitHub Pages** dans les paramètres du repo (Settings > Pages > Source: branche main)
7. Ouvrir `communication.html` sur les deux téléphones, choisir son identité, tester

## Personnaliser

- Les couleurs sont dans `communication.css` : `.yellow`, `.green`, `.red` pour les boutons/voyants, `#0a1929` pour le fond
- Pour ajouter/retirer un état (ex: un 6ᵉ bouton), dupliquer un `<button class="action-btn ...">` dans `communication.html` et son équivalent `<div class="indicator ...">` dans la section Reçu, avec le même `data-val`

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

