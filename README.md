# assistant-message

Ce plugin de [assistant-plugins](https://aymkdn.github.io/assistant-plugins/) permet de lire un fichier ics et de lancer une notification sur les Google Home.

## Pré-requis
Avant toutes choses, il est nécessaire d'installer `assistant-plugins` et le plugin `assistant-notifier`. Vous devrez les configurer correctement pour profiter pleinement du présent plugin.

## Installation

Si vous n'avez pas installé `assistant-plugins`, alors il faut le faire, et sélectionner __message__ comme plugin.

Si vous avez déjà installé `assistant-plugins`, et que vous souhaitez ajouter ce plugin, alors :

* Pour Windows, télécharger install_message.bat dans le répertoire `assistant-plugins`, puis l'exécuter en double-cliquant dessus.
* Pour Linux/MacOS, ouvrir une console dans le répertoire `assistant-plugins` et taper :
`npm install assistant-message@latest --save && npm run-script postinstall`

## Configuration

Éditer le fichier `configuration.json` du répertoire assistant-plugins et y indiquer l'url vers votre fichier ics en ligne. Exemple :

```
    "message": {
      "ics": "https://calendar.google.com/calendar/ical/32ph4p3h4i23u29i4bvkbef%40group.calendar.google.com/private-23hpdfp240o04nl2nvp094jolzef/basic.ics"
    }
```

## Utilisation

Une fois configurée, le plugin lira toutes les minutes le fichier ICS indiqué. A chaque événement commençant le jour même à l'heure de sa lecture (cf. chaque minute), le plugin enverra une commande à `assistant-notifier` sour la forme :
```
notifier_{google_home_id} mon message
```

Pour se faire, vous devez respecter les règles suivantes :
* Le titre de l'événement sera le texte diffusé votre ou vos Google Home
* le descriptif _(ou les notes selon votre gestionnaire de calendrier)_ contiendra le ou les noms de Google Home désiré(s). Ces noms sont ceux que vous aurez indiqué dans votre configuration du plugin `assistant-notifier`


## Remarque

Ce plugin n'offre pas de `commande` utilisable par PushBullet car tout se fait de façon indépendante de la plateforme en local sur votre machine.