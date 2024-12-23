﻿<h1>Eliana-Advanced-WhatsApp-Bot</h1>

A sophisticated WhatsApp bot built with Node.js that features AI chat capabilities (using Gemini AI), Facebook video downloads, and an intelligent command system. The bot uses QR code authentication and supports both English and Bengali languages.

![License](https://img.shields.io/badge/license-MIT-blue.svg)
![Node](https://img.shields.io/badge/node-%3E%3D16.0.0-brightgreen.svg)
![WhatsApp Web.js](https://img.shields.io/badge/whatsapp--web.js-latest-green.svg)

**If any api keys are not work please contact me on telegram**:
```url
https://t.me/BD_NOOBRA
```

## 📁 Project Structure
```
eliana-whatsapp-bot/
├── package.json
├── bot.js                 # Main bot initialization and message handler
├── config.json           # Configuration file for API keys and settings
├── utils/
│   └── messageUtils.js    # Utility functions for admin checks
└── scripts/
    ├── commands/         # Command modules
    │   ├── ai.js         # Gemini AI integration
    │   ├── chat.js       # General chat functionality
    │   ├── fbdl.js       # Facebook video downloader
    │   └── help.js       # Help command with multi-language support
    └── events/
        └── ready.js      # Bot ready event handler
```

## 🚀 Features

- **Multi-Language Support**: Built-in support for English and Bengali
- **AI Integration**: 
  - Gemini AI for intelligent responses
  - Natural chat capabilities
- **Media Handling**: 
  - Facebook video download functionality
  - Supports both high and low quality video downloads
- **Command System**:
  - Prefix and non-prefix commands
  - Category-based command organization
  - Detailed help system
- **Admin Controls**:
  - Admin-only commands
  - Owner privileges
  - Permission system

## 📋 Installation

1. **Initialize Project**:
```bash
mkdir eliana-whatsapp-bot
cd eliana-whatsapp-bot
npm init -y
```

2. **Install Dependencies**:
```bash
npm install whatsapp-web.js qrcode-terminal node-fetch
```

3. **Configuration Setup**:

Create `config.json` with your API keys:
```json
{
    "botOwnerName": "YourName",
    "ownerNumber": "YourNumber",
    "adminNumbers": ["ADMIN_1_Number", "ADMIN_2_NUMBER"],
    "prefix": "!",
    "botName": "BotName",
    "language": "en",
    "geminiApiKey": "na_T51VHMGBMZJO7S2B",
    "nexaloApiKey": "na_T51VHMGBMZJO7S2B"
}


```

## 🤖 Command Details

### AI Command (ai.js)
```javascript
Usage: !ai <question>
Description: Integrates with Gemini AI for intelligent responses
Example: !ai What is quantum computing?
```

### Chat Command (chat.js)
```javascript
Usage: Just send any message
Description: Natural conversation without prefix
Example: Hello, how are you?
```

### Facebook Downloader (fbdl.js)
```javascript
Usage: !fbdl <video_url>
Description: Downloads Facebook videos in highest quality
Example: !fbdl https://facebook.com/watch?v=123456
```

### Help Command (help.js)
```javascript
Usage: !help [command_name]
Description: Shows all commands or detailed info about specific command
Example: !help fbdl
```

## 🔧 Key Components

### 1. Main Bot Handler (bot.js)
- Initializes WhatsApp client with LocalAuth
- Dynamically loads commands and events
- Handles message routing and command execution
- Implements permission checks

### 2. Command Structure
Each command module follows this structure:
```javascript
module.exports = {
    name: 'command_name',
    category: 'Category',
    prefix: true/false,
    description: 'Command description',
    guide: {
        bn: 'Bengali guide',
        en: 'English guide'
    },
    author: 'Author name',
    adminOnly: false,
    execute: async function(message, args, client) {
        // Command logic
    }
}
```

## 📝 Command Categories

1. **AI**
   - `ai`: Gemini AI integration
   - `chat`: Natural conversation

2. **Utility**
   - `help`: Command information
   - `fbdl`: Facebook video downloader

## ⚙️ Advanced Features

### Multi-Language Support
The bot supports dynamic language switching:
```javascript
const language = config.language || 'en';
message.reply(command.guide[language]);
```

### Permission System
```javascript
if (command.adminOnly && !client.isAdmin(message.from)) {
    return message.reply('You do not have permission to use this command.');
}
```

### Dynamic Command Loading
```javascript
fs.readdirSync(commandsPath).forEach(file => {
    if (file.endsWith('.js')) {
        const command = require(path.join(commandsPath, file));
        client.commands.set(command.name, command);
    }
});
```

## 🔒 Security Features

1. **Authentication**
   - Uses WhatsApp's official QR code authentication
   - Implements LocalAuth for session persistence
   - Secure session management

2. **Permission Levels**
   - Owner privileges
   - Admin-only commands
   - Regular user restrictions

## 🛠️ Error Handling

The bot implements comprehensive error handling:
```javascript
try {
    await command.execute(message, args, client);
} catch (error) {
    console.error(error);
    await message.reply('There was an error executing that command.');
}
```

## 📊 Monitoring

Key areas monitored:
- Command execution success/failure
- API responses
- Message processing
- Authentication status

## 🔄 Future Improvements

1. **Planned Features**
   - Database integration
   - More AI providers
   - Advanced media handling
   - User statistics

2. **Optimization Areas**
   - Rate limiting
   - Cache implementation
   - Response time improvement

## 🆘 Troubleshooting

Common issues and solutions:

1. **Authentication Failed**
   ```bash
   rm -rf .wwebjs_auth
   node bot.js
   ```

2. **API Errors**
   - Verify API keys in config.json
   - Check API endpoint status
   - Confirm network connectivity
  
## 🔧 Configuration Options

| Option | Description | Required |
|--------|------------|----------|
| `prefix` | Command prefix (e.g., "!") | Yes |
| `geminiApiKey` | API key for Gemini AI | Yes |
| `nexaloApiKey` | API key for Nexalo services | Yes |
| `language` | Default language (en/bn) | Yes |
| `ownerNumber` | Bot owner's WhatsApp number | Yes |

## 📚 API Documentation

### Gemini AI API
Endpoint: `https://api.nexalo.xyz/gemini`
Parameters:
- `api`: Your Gemini API key
- `text`: The question to ask

### Facebook Download API
Endpoint: `https://api.nexalo.xyz/fbdl`
Parameters:
- `api`: Your Nexalo API key
- `url`: Facebook video URL

## 🔐 Best Practices

1. **Security**
   - Never commit config.json
   - Regularly rotate API keys
   - Implement rate limiting

2. **Performance**
   - Handle large files appropriately
   - Implement timeouts
   - Monitor memory usage

## 📝 Contributing

1. Fork the repository
2. Create feature branch
3. Commit changes
4. Push to branch
5. Create Pull Request

---


<h2 align="left">⚡️ Connect with me</h2>
  <table border="1" cellpadding="10" cellspacing="0">
    <tr>
      <th>Discord</th>
      <th>Telegram</th>
      <th>Instagram</th>
      <th>YouTube</th>
    </tr>
    <tr>
      <td align="center">
        <img src="https://github.com/user-attachments/assets/6b381b30-861d-4a3c-859a-367da4956347" alt="Facebook QR" width="150"><br>
        <a href="https://discord.gg/yfBx5GU9Xr">Eliana Support Server</a>
      </td>
      <td align="center">
        <img src="https://github.com/user-attachments/assets/0bd6fcf3-332b-400b-8edf-0aa613c2d7bc" alt="Telegram QR" width="150"><br>
        <a href="https://t.me/BD_NOOBRA">BD_NOOBRA</a>
      </td>
      <td align="center">
        <img src="https://github.com/user-attachments/assets/727d205c-3f31-494b-ba2e-a594122d2b20" alt="Twitter QR" width="150"><br>
        <a href="https://www.instagram.com/hridoycode/">HridoyCode</a>
      </td>
      <td align="center">
        <img src="https://github.com/user-attachments/assets/f9dedbbb-606c-4ab5-b67b-73ab2f640ebb" alt="YouTube QR" width="150"><br>
        <a href="https://www.youtube.com/@hridoy-code">Hridoy Code</a>
      </td>
    </tr>
  </table>

For complete code and updates, visit the [GitHub repository](https://github.com/1dev-hridoy/eliana-whatsapp-bot).
