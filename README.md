kiconst prefix = '.';lezkushCypherX/
├── commands/
│   ├── admin/
│   │   └── ban.js
│   ├── media/
│   │   └── play.js
│   ├── fun/
│   │   └── ping.js
│   └── ...
├── index.js
└── package.json







Here are some ideas to get you started:

- 🔭 I’m currently working on ...
- 🌱 I’m currently learning ...
- 👯 I’m looking to collaborate on ...
- 🤔 I’m looking for help with ...
- 💬 Ask me about ...
- 📫 How to reach me: ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...
-->
const prefix = '.'



module.exports = {
    name: 'ban',
    description: 'Ban user from bot',
    execute(message, args) {
        message.reply('User has been banned!');
    }
};



const fs = require('fs');
const path = require('path');
const { Client } = require('whatsapp-web.js');
const qrcode = require('qrcode-terminal');

const client = new Client();
const prefix = '.';
client.commands = new Map();

// Load all commands from folders
const commandFolders = fs.readdirSync('./commands');
for (const folder of commandFolders) {
    const commandFiles = fs.readdirSync(`./commands/${folder}`).filter(file => file.endsWith('.js'));
    for (const file of commandFiles) {
        const command = require(`./commands/${folder}/${file}`);
        client.commands.set(command.name, command);
    }
}

client.on('qr', qr => {
    qrcode.generate(qr, { small: true });
});

client.on('ready', () => {
    console.log('lezkushCypherX is ready!');
});

client.on('message', message => {
    if (!message.body.startsWith(prefix)) return;

    const args = message.body.slice(prefix.length).trim().split(/ +/);
    const commandName = args.shift().toLowerCase();

    const command = client.commands.get(commandName);
    if (!command) return;

    try {
        command.execute(message, args);
    } catch (error) {
        console.error(error);
        message.reply('Kuna kosa limetokea!');
    }
});

client.initialize();

