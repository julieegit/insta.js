# Insta.js

💬 Object-oriented library for sending and receiving messages via Instagram! Based on **[instagram-private-api](https://github.com/dilame/instagram-private-api)** and made for the **[PronoteBot](https://github.com/Androz2091/pronote-bot)** project.

## Example

Here is a simple chatbot made with the library:

```js
const Insta = require('@androz2091/insta.js');

const client = new Insta.Client();

client.on('connected', () => {
    console.log(`Logged in as ${client.user.username}`);
});

client.on('messageCreate', (message) => {
    if (message.authorID === client.user.id) return

    message.markSeen();

    if (message.content === '!ping') {
        message.author.send('!pong');
    }
});

client.on('messageDelete', (cachedMessage) => {
    if (!cachedMessage) return;
    console.log(`@${cachedMessage.author.username} has just deleted their message: ${cachedMessage.content}`);
});

client.login('username', 'password');
```

## To do

* Improve `User` and `ClientUser` classes by supporting all the properties sent by the API

## Credits

🧡 Big thanks to **[Nerixyz](https://github.com/Nerixyz)** and **[dilame](https://github.com/dilame)** for their libraries.
