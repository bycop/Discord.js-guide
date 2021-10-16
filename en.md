# Discord.js Guide
Welcome on the English version guide, here you will learn how to create your first bot, how to invite it on servers and how to host it 24h/24 for free.

## Summary

1. [Requirements](https://github.com/bycop/discord.js-guide/blob/master/en.md#requirements)
2. [Creation of the token](https://github.com/bycop/discord.js-guide/blob/master/en.md#creation-of-the-token)
3. [Creation of your first command](https://github.com/bycop/discord.js-guide/blob/master/en.md#creation-of-your-first-command)
5. [How to host the bot for free](https://github.com/bycop/discord.js-guide/blob/master/en.md#creation-of-the-token)

## Requirements

First of all, you will need several things essential to your bot creation: 
- Node.js
- A text editor (IDE)

Later on you will need other things but we'll find out as we go along.

### Installation de Node.js

First go to https://nodejs.org/en/download/ and then click on "Windows Installer" if you are on Windows, for other platforms the process is the same.
<br><br>
Once this is done, you will need to open the .msi you just downloaded and click on next until the installation is complete.
<br><br>
In order to test if Node.js is well installed, open a CMD Terminal (Start menu then CMD) and do the command "node --version".
Normally, the version number should be returned by the terminal.

### Installation d'un IDE.

In order to create your bot as well as code it, you will need a good text editor. For the blow I advise you Visual studio code which is very simple of use while being very complete. 
<br><br>
To download it is like for Node.js, go to https://code.visualstudio.com/ then click on Download for Windows. Once this is done, run the .exe download then do the following until the end of the installation.

## Creation of the token

After downloading and installing Node.js and Visual studio code, you will need a bot token. To do so, go to https://discord.com/developers/applications/ and click in the upper right corner on "New Application". Enter a name and click "Create". Feel free to put a profile picture and a description.
<br><br>
To get the token, go to bot and create the bot. You will have a token hidden under "Click to Reveal token" below the name of your bot. Click on "Copy" then write it down somewhere to keep it handy.

## Creation of your first command

Launch Visual studio code then do "Open a folder", choose a folder to work in then open it.
<br><br>
At the top of the window you will have a "Terminal" tab, click on it and then do "New Terminal".
Once on the terminal window, run the "npm init" command and enter until you are asked to write "yes", write it and then enter again.
In the same window, run the command "npm install discord.js" to install the discordjs library which will allow us to work easily with the Discord api.
<br><br>
```javascript
const Discord = require('discord.js');
```
The first line of our bot will be the one that will define the keyword "Discord" in order to be able to call it later.
```javascript
const bot = new Discord.Client({intents: [Intents.FLAGS.GUILDS, Intents.FLAGS.GUILD_MESSAGES]});
```
This second line, uses the Discord created above to create the bot itself.
```javascript
bot.login("TOKEN");
```
It is on this line that we will connect with our bot created before on the discord developpers website. Just enter the token and continue.
```javascript
bot.on("ready", () => {
	console.log("Bot Ready");
})
```
Thanks to this first "Event" we will detect if the bot manages to connect correctly to Discord, once it is connected it will write "Bot ready" in the debugging console.
<br><br>
Let's test it! 
<br>
Just press F5 on your keyboard and wait for the message in the console, there will be either an error in red or our message "Bot Ready".
<br><br>
And our first order? 
<br>
Let's go ! 
```javascript
bot.on("message", (message) => {
	if (message.content === "!ping")
		message.channel.send("Pong !");
})
```
This time we create the message event that will intervene each time a message is received by the bot, if a person sends the message "!ping" the bot will reply with "Pong!".

## How to host the bot for free

After creating a real bot that works (not just the !ping above), you'll want to share it with everyone, right? But in order to share it, you have to turn it on!
<br><br>
You will need to create a file named "Procfile" with in it only the line
```
Worker : node index.js
```
Then go to https://heroku.com/ and create an account.
Then click on "new->app" on the dashboard or go on this page directly https://dashboard.heroku.com/new-app, indicate a name and a hosting region (Europe) then do "Create app".
<br>
Follow the Heroku installation procedure on this page https://devcenter.heroku.com/articles/heroku-cli.
then once this is done run the command heroku login in the vscode terminal. A window will open, allow the connection and then close it directly.
<br>
Install Git now on your machine through this link https://git-scm.com/downloads same as above, click next and finish the installation.
<br>
Normally you will be able to do the "git init" command in the vscode terminal. If you can't, restart vscode and try again.
<br>
Once the "git init" command is done, it's the turn of "git add index.js" to make its entry. Followed by "git add package.json" and "git add package-lock.json".
To record all this do "git commit -m push" then "heroku git:remote -a <Name of the bot filled in on Heroku>" then "git push heroku master". The detail of the commands is on the Deploy page of the heroku dashboard.
<br><br>
After a few seconds, in the "Resources" tab of Heroku, 2 switches appeared, uncheck "npm start" and check "node index.js". Then click on "More" at the top right and then "Restart all dynos".

You just have to invite your bot on your server. Go back to the developer discord page then copy the client ID of the bot in the General information tab. https://discord.com/oauth2/authorize?client_id=CLIENTID&scope=bot then copy this link by replacing CLIENTID by the number copied just before. Choose the server on which the guest is running and test if everything works.

Normally your bot is online and ready to play ping pong with you.

If you have problems, don't hesitate to create an Issue.
Thank you for your reading.
