# Guide Discord.js
Bienvenue sur le guide version française, ici vous allez apprendre à créer votre premier bot, à l'inviter sur des serveurs ainsi qu'à l'héberger 24h/24 gratuitement.

## Sommaire

1. [Prérequis](https://github.com/bycop/discord.js-guide/blob/master/fr.md#pr%C3%A9requis)
2. [Création du token](https://github.com/bycop/discord.js-guide/blob/master/fr.md#cr%C3%A9ation-dun-token)
3. [Création de votre première commande](https://github.com/bycop/discord.js-guide/blob/master/fr.md#cr%C3%A9ation-de-votre-premi%C3%A8re-commande)
5. [Comment héberger le bot gratuitement](https://github.com/bycop/discord.js-guide/blob/master/fr.md#comment-h%C3%A9berger-le-bot-gratuitement)

## Prérequis

Avant toute chose, vous allez avoir besoin de plusieurs choses essentielles à votre création de bot : 
- Node.js
- Un éditeur de texte (IDE)

Par la suite vous aurez besoin d'autres choses mais on découvrira ça au fur et à mesure.

### Installation de Node.js

Rendez vous premièrement sur https://nodejs.org/en/download/ puis, cliquez sur "Windows Installer" si vous êtes sur Windows, pour les autres plateformes le procédé est le même. <br><br>
Une fois cela fait, vous allez devoir ouvrir le .msi que vous venez de télécharger puis cliquer sur suivant jusqu'à la fin de l'installation.
<br><br>
Afin de testé si Node.js est bien installer, ouvrez un Terminal CMD (Menu démarrer puis CMD) et faites la commande "node --version".
Normalement, le numéro de version devrait être renvoyer par le terminal.

### Installation d'un IDE.

Afin de créer votre bot ainsi que de le coder, vous allez avoir besoin d'un bon éditeur de texte. Pour le coup je vous conseil Visual studio code qui est très simple d'utilisation en étant très complet. 
<br><br>
Pour le télécharger c'est comme pour Node.js, rendez vous sur https://code.visualstudio.com/ puis cliquez sur Download for Windows. Une fois cela fait, executez le .exe télécharger puis faites suivant jusqu'à la fin de l'installation.

## Création d'un token

Après avoir télécharger et installer Node.js et Visual studio code, vous allez avoir besoin d'un token de bot. Pour cela, rendez vous sur https://discord.com/developers/applications/ puis cliquez dans le coin supérieur droit sur "New Application". Indiquez un nom puis faites "Create". Libre à vous de mettre une photo de profil ainsi qu'une description.
<br><br>
Pour obtenir le token, rendez vous dans bot puis créer le bot. Vous aurez un token caché sous "Click to Reveal token" en dessous du nom de votre bot. Cliquez sur "Copy" puis notez le quelque part de manière à le garder sous la main.

## Création de votre première commande

Lancez Visual studio code puis faites "Ouvrir un dossier", choisissez un dossier pour travailler puis ouvrez le.
<br><br>
Dans le haut de la fenêtre vous aurez un onglet "Terminal", cliquez dessus puis faites "Nouveau terminal".
Une fois sur la fenêtre de terminal, lancez la commande "npm init" puis faites entrer jusqu'au moment où il est demandé d'écrire "yes", écrivez-le puis faites entrer à nouveau.
Dans cette même fenêtre, lancez la commande "npm install discord.js" afin d'installer la librairie discordjs qui va nous permettre de travailler facilement avec l'api Discord.
<br><br>
```javascript
const Discord = require('discord.js');
```
La première ligne de notre bot sera celle qui va définir le mot clé "Discord" afin de pouvoir l'appeler plus tard.
```javascript
const bot = new Discord.Client();
```
Cette seconde ligne, se sert du Discord créer au-dessus pour créer le bot en lui même.
```javascript
bot.login("TOKEN");
```
C'est sur cette ligne que nous allons nous connecter avec notre bot créer auparant sur le site de discord developpers. Indiquez simplement le token puis passez à la suite.
```javascript
bot.on("ready", () => {
	console.log("Bot Prêt");
})
```
Grâce à ce premier "Event" nous allons détecter si le bot parvient à se connecter correctement à Discord, une fois qu'il sera connecter, il écrira "Bot prêt" dans la console de debogage.
<br><br>
Testons ça ! 
<br>
Appuyez simplement sur F5 sur votre clavier puis attendez le message dans la console, il y aura soit une erreur en rouge, soit notre message "Bot Prêt".
<br><br>
Et notre première commande ? 
<br>
Allons-y ! 
```javascript
bot.on("message", (message) => {
	if (message.content === "!ping")
		message.channel.send("Pong !");
})
```
Cette fois-ci, on créer l'event message qui va intervenir à chaque fois qu'un message sera reçu par le bot, si une personne envoie le message "!ping" le bot répondra par "Pong !".

## Comment héberger le bot gratuitement

Après avoir créer un vrai bot qui marche (pas seulement le !ping ci-dessus), vous allez avoir envie de le partager à tout le monde non ? Mais pour le partager il faut qu'il soit allumer !
<br><br>
Vous allez avoir besoin de créer un fichier nommé "Procfile" avec dedans seulement la ligne
```
Worker : node index.js
```
Ensuite rendez-vous sur https://heroku.com/ puis créez vous un compte.
Ensuite cliquez sur "new->app" sur le tableau de bord ou rendez vous sur cette page directement https://dashboard.heroku.com/new-app, indiquez un nom et une région d'hébergement (Europe) puis faites "Create app".
<br>
Suivez la procédure d'installation d'Heroku sur cette page https://devcenter.heroku.com/articles/heroku-cli
puis une fois cela fait lancez la commande heroku login dans le terminal vscode. Une fenêtre va s'ouvrir, autorisez la connexion puis fermez celle-ci directement.
<br>
Installer maintenant Git sur votre machine grâce à ce lien https://git-scm.com/downloads pareil qu'au-dessus, cliquez sur suivant puis finissez l'installation.
<br>
Normalement vous pourrez faire la commande "git init" dans le terminal vscode. Si vous ne pouvez pas, redémarrez vscode puis réessayer.
<br>
Une fois la commande "git init" faite, au tour de "git add index.js" de faire son entrée. Suivie de "git add package.json" et de "git add package-lock.json".
Pour enregistrer tout cela faites "git commit -m push" puis "heroku git:remote -a <Nom du bot renseigné sur Heroku>" puis "git push heroku master". Le détail des commandes est sur la page Deploy du tableau de bord heroku.
<br><br>
Après quelques secondes, dans l'onglet "Resources" d'Heroku, 2 interrupteurs sont apparus, décochez "npm start" et cochez "node index.js". Par la suite cliquez en haut à droite sur "More" puis "Restart all dynos".

Il vous reste plus qu'à inviter votre bot sur votre serveur. Retournez sur la page developer discord puis copié le client ID du bot dans l'onglet General information. https://discord.com/oauth2/authorize?client_id=CLIENTID&scope=bot puis copiez ce lien en remplaçant CLIENTID par le nombre copié juste avant. Choisissez le serveur sur lequel l'invité puis testé si tout fonctionne.

Normalement votre bot est en ligne et prêt à jouer au ping pong avec vous.

Si vous avez des problèmes, n'hésitez pas à créer une Issue.
Merci de votre lecture.