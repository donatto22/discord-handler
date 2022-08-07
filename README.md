# Ax `Discord` Handler
An easy way to make an event and command handler on discord

<a href="https://www.npmjs.com/package/ax-handler"><img src="https://img.shields.io/npm/v/ax-handler?style=flat-square" alt="version">

```js
const handler = require('ax-handler')
```

## Use example
You only need one function to handler your slash commands and events

```js
// The first parameter, is the discord client
// Second parameter, is the path of your folder
handler.eventhandler(client, path.join(__dirname, 'events'))
```

```js
// The first parameter is the path of the folder
// Second parameter is the collection of slash commands
// If you have subfolders, set the third parameter on true
client.slashcommands = new Collection()
handler.slashhandler(path.join(__dirname, 'slashcmd'), client.slashcommands, true)
```

### Output
```mkd
> Bot is ready
> Slashcommands loaded successfully
```

### What do I need?
- First, the name you put in handler has to be the same as the name of your folder
- Second, for event and slash handler you need a **run** function

### Example
```js
// folder / subfolder / file
// slashcmd / util/ ping.js
const { SlashCommandBuilder } = require('@discordjs/builders')

module.exports = {
    data: new SlashCommandBuilder().setName('ping'),

    async run (client, interaction) {
        // code
    }
}
```

```js
// folder / file
// events / ready.js
const { ActivityType, Client, Message } = require('discord.js')

module.exports = {
    name: 'ready',

    async run (client, message) {
        client.user?.setPresence({
            activities: [{ 
                name: 'Using ax-handler', 
                type: ActivityType.Playing 
            }]
        })
    }
}
```