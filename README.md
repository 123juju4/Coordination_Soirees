# Régie mariage — synchro en temps réel

Deux pages HTML synchronisées via Firebase Realtime Database :
- `regie.html` + `regie.css` : pilotage (étape en cours + message rapide)
- `affichage.html` + `affichage.css` : lecture seule, à afficher côté sono/coulisse

## Mise en route (5 minutes)

1. Créer un projet sur https://console.firebase.google.com
2. Dans le projet, aller dans **Build > Realtime Database** > "Créer une base de données" > démarrer en **mode test**
3. Dans **Paramètres du projet > Général**, ajouter une application Web, copier la config
4. Coller cette config dans `firebase-config.js` (remplacer les valeurs `TON_...`)
5. Mettre les 5 fichiers (`regie.html`, `regie.css`, `affichage.html`, `affichage.css`, `firebase-config.js`) dans un repo GitHub
6. Activer **GitHub Pages** dans les paramètres du repo (Settings > Pages > Source: branche main)
7. Ouvrir `regie.html` sur un appareil et `affichage.html` sur un autre : tester que ça se synchronise

## Personnaliser

- La liste des étapes est modifiable directement dans `regie.html`, tableau `ETAPES` (ligne ~120)
- Les couleurs sont dans `regie.css` et `affichage.css` (variables simples à changer : `#e0c9a6` = couleur dorée, `#1a1a2e` = fond)

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
