## Hi there 👋
mkdir lezkushCypherX
cd lezkushCypherX
<!--
**lezkush8/lezkush8** is a ✨ _special_ ✨ repository because its `README.md` (this file) appears on your GitHub profile.

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
const prefix = '.';




npm init -y
npm install whatsapp-web.js


touch index.js





const { Client } = require('whatsapp-web.js');
const qrcode = require('qrcode-terminal');

const client = new Client();

client.on('qr', (qr) => {
    // Display QR code for WhatsApp login
    qrcode.generate(qr, { small: true });
});

client.on('ready', () => {
    console.log('Bot is ready!');
});

client.on('message', message => {
    const prefix = '.';

    // Check if message starts with dot (.)
    if (message.body.startsWith(prefix)) {
        const args = message.body.slice(prefix.length).trim().split(/ +/);
        const command = args.shift().toLowerCase();

        // Example command: .ping
        if (command === 'ping') {
            message.reply('Pong!');
        }
        // Add more commands here...
    }
});

client.initialize();


node index.js

.ping

if (command === 'ban') {
    // Logic ya ban command
    message.reply('User has been banned!');
} else if (command === 'play') {
    // Play music or video logic
    message.reply('Playing music...');
}
// Continue adding more commands

