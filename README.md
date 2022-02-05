# smart-chatbot
<a href="https://npmjs.com/package/smart-chatbot" rel="nofollow"><img src="https://img.shields.io/npm/dt/smart-chatbot.svg?style=for-the-badge" alt="npm"></a><a href="https://npmjs.com/package/smart-chatbot" rel="nofollow"><img src="https://img.shields.io/npm/v/smart-chatbot.svg?style=for-the-badge" alt="npm"></a>

**Examples:**
```js
const chatbot = require("smart-chatbot");
const chatclient = new chatbot.Client("SECRET KEY", "BOT NAME");

chatclient.chat({
	message: "Hello",
	user: "SECRET USER ID"
}).then(answer => console.log);
```
<br>
Discord Bot (tag) Message Chatbot
```js
const Discord = require("discord.js");
const client = new Discord.Client({
  partials: ["MESSAGE", "CHANNEL"],
  intents: [
    Discord.Intents.FLAGS.GUILDS,
    Discord.Intents.FLAGS.GUILD_MESSAGES,
  ]
});
const chatbot = require("smart-chatbot"); 
const chatclient = new chatbot.Client("SECRET KEY", "BOT NAME");

client.on("message", async(message) => {
  if(!message || !message.content || !message.author || message.author.bot) return;
  
  if (message.content.startsWith(`<@${client.user.id}>`) || message.content.startsWith(`<@!${client.user.id}>`)) {
       let args = message.content.split(" ").slice(1);
       let soru = args.slice(0).join(' ');

       let reply = await chatclient.chat({ 
           message: soru, 
           user: message.author.id 
        });
     message.channel.send(reply);
  }
});

client.login("SECRET DISCORD BOT TOKEN");
```
<br>

**What is SECRET KEY?**

For Secret Key Join Server: https://discord.gg/gkmwaAZQBu
