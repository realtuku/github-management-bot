# 🤖 GitHub Management Bot

<div align="center">

[![GitHub stars](https://img.shields.io/github/stars/realtuku/github-mng-bot?style=for-the-badge&logo=github)](https://github.com/realtuku/github-mng-bot/stargazers)
[![GitHub forks](https://img.shields.io/github/forks/realtuku/github-mng-bot?style=for-the-badge&logo=github)](https://github.com/realtuku/github-mng-bot/network)
[![GitHub issues](https://img.shields.io/github/issues/realtuku/github-mng-bot?style=for-the-badge&logo=github)](https://github.com/realtuku/github-mng-bot/issues)
[![GitHub license](https://img.shields.io/github/license/realtuku/github-mng-bot?style=for-the-badge)](https://github.com/realtuku/github-mng-bot/blob/main/LICENSE)
[![Telegram](https://img.shields.io/badge/Telegram-Bot-blue?style=for-the-badge&logo=telegram)](https://t.me/GitHubmngbot)
[![Node.js](https://img.shields.io/badge/Node.js-18.x-green?style=for-the-badge&logo=nodedotjs)](https://nodejs.org/)
[![MongoDB](https://img.shields.io/badge/MongoDB-Atlas-green?style=for-the-badge&logo=mongodb)](https://www.mongodb.com/cloud/atlas)

A powerful Telegram bot for complete GitHub repository management. Manage your repositories, files, and collaborate seamlessly directly from Telegram.

[✨ Live Demo](https://githubmng-xmn.onrender.com) · [📚 Documentation](https://githubmng-xmn.onrender.com) · [🐛 Report Bug](https://github.com/realtuku/github-mng-bot/issues) · [💡 Request Feature](https://github.com/realtuku/github-mng-bot/issues)

</div>

## ✨ Features

### 📁 Repository Management
- **List Repositories**: View all your GitHub repositories with details
- **Create Repos**: Create new repositories with custom settings
- **Edit Repositories**: Update repository name, description, and settings
- **Delete Management**: Full control over your repositories

### 📄 File Operations
- **Browse Files**: Navigate through repository files and directories
- **Upload Files**: Upload multiple files to any repository
- **Delete Files**: Remove files with confirmation
- **File Management**: Complete file operations from Telegram

### 🔐 Security & Integration
- **OAuth 2.0**: Secure GitHub authentication
- **Token Management**: Encrypted token storage
- **Session Security**: Protected user sessions
- **Rate Limiting**: Respect GitHub API limits

### 🚀 Advanced Features
- **Real-time Sync**: Instant updates between Telegram and GitHub
- **Inline Keyboard**: Interactive buttons for easy navigation
- **Multi-language Support**: Built for global users
- **Error Handling**: Comprehensive error management
- **Health Check Monitoring**: Includes `/health` for uptime monitors like UptimeRobot

## 🎯 Quick Start

### Prerequisites
- Node.js 18.x or higher
- MongoDB Atlas account
- Telegram Bot Token (from [@BotFather](https://t.me/BotFather))
- GitHub OAuth App credentials

### Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/realtuku/github-mng-bot.git
   cd github-mng-bot
   ```

2. **Install dependencies**
   ```bash
   npm install
   ```

3. **Configure environment variables**
   ```bash
   cp .env.example .env
   ```

   Edit `.env` with your credentials:
   ```env
   PORT=3000
   NODE_ENV=production
   TELEGRAM_BOT_TOKEN=your_telegram_bot_token
   GITHUB_CLIENT_ID=your_github_client_id
   GITHUB_CLIENT_SECRET=your_github_client_secret
   MONGODB_URI=your_mongodb_connection_string
   SESSION_SECRET=your_session_secret
   JWT_SECRET=your_jwt_secret
   FRONTEND_URL=your_frontend_url
   WEBHOOK_URL=your_webhook_url
   AGREEMENT_URL=your_agreement_url
   BOT_USERNAME=your_bot_username
   ```

4. **Start the application**
   ```bash
   npm start
   ```

## 🩺 Render / UptimeRobot Health Check

Render's free web services can sleep after inactivity if no external monitor pings them.
This app includes a health endpoint that is designed for uptime monitoring.

### Endpoint
- `GET /health` → returns JSON status
- `HEAD /health` → lightweight status check for uptime services

Example response:
```json
{
  "status": "ok",
  "timestamp": "2025-12-05T10:30:00.000Z",
  "service": "GitHub Management Bot",
  "uptime": 3600
}
```

### Why this matters
Render free instances may go to sleep if they are not actively monitored.
If you want your service to stay alive 24/7, monitor it with an external uptime service.

### Recommended setup
Use UptimeRobot (free plan) with this URL:
```text
https://your-render-service.onrender.com/health
```

Recommended monitor settings:
- Monitor type: HTTP(s)
- URL: `https://your-render-service.onrender.com/health`
- Interval: every 5 minutes

This will ping the service regularly and prevent the free Render instance from sleeping.

## 📱 Bot Commands

```
/start - Start the bot and show main menu
/connect - Connect GitHub account
/repos - List all your GitHub repositories
/createrepo - Show options to create a new repository
/newrepo [name] [description] [private] - Create a repository
/files - File management options
/listfiles [owner/repo] - List files in a repository
/deletefile [owner/repo] [file-path] - Delete a file
/about - About the bot and developer info
/help - Show all available commands
```

## 🔧 API Endpoints

### Health Check
- `GET /health` - Get service health status
- `HEAD /health` - Quick health check for monitoring services

### User Management
- `POST /api/user/agree` - Accept terms and conditions
- `GET /api/user/:telegramId` - Get user information

### GitHub Integration
- `GET /auth/github` - Initiate GitHub OAuth flow
- `GET /auth/github/callback` - GitHub OAuth callback
- `POST /api/github/repos` - Fetch user's repositories

### Web Pages
- `GET /` - Agreement page
- `GET /agreement` - User agreement
- `GET /success` - Success page after OAuth
- `GET /error` - Error page

## 🏗️ Project Structure

```
github-mng-bot/
├── index.js                 # Main application file
├── agreement.html           # User agreement page
├── success.html             # OAuth success page
├── error.html               # Error page
├── render.yaml              # Render deployment config
├── package.json             # Project dependencies
├── .env.example             # Environment variables template
├── README.md                # Project documentation
└── data.json                # Local cache file used for persistence
```

## 🗄️ Database Schema

### User Model
```javascript
{
  telegramId: String (unique),
  githubId: String,
  githubAccessToken: String,
  githubUsername: String,
  isAgreed: Boolean,
  isConnected: Boolean,
  createdAt: Date,
  lastActive: Date,
  repositories: [{
    name: String,
    full_name: String,
    url: String,
    private: Boolean
  }]
}
```

## 🔒 Security Features

- **OAuth 2.0 Authentication**: Secure GitHub integration
- **Token Encryption**: GitHub access tokens are securely stored
- **Session Management**: User sessions are protected
- **Rate Limiting**: Respects GitHub API rate limits
- **Webhook Verification**: Secure webhook handling

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## 📝 License

This project is licensed under the MIT License - see the LICENSE file for details.

## 👨‍💻 Developer

**Ximanta** (realtuku)

- 🔗 Portfolio: [ximanta.onrender.com](https://ximanta.onrender.com)
- 📧 Email: xiimnta@outlook.com
- 💬 Telegram: [@tukuexe](https://t.me/tukuexe)
- 🐙 GitHub: [@realtuku](https://github.com/realtuku)

## 🙏 Acknowledgments

- [Telegraf](https://telegraf.js.org/) - Telegram Bot Framework
- [GitHub API](https://docs.github.com/en/rest) - GitHub Integration
- [MongoDB](https://www.mongodb.com/) - Database
- [Express.js](https://expressjs.com/) - Web Framework
- [Render](https://render.com/) - Hosting Platform

## 📧 Support

For issues, questions, or suggestions, please:
- Create an [Issue](https://github.com/realtuku/github-mng-bot/issues)
- Contact via [Telegram](https://t.me/tukuexe)
- Email: xiimnta@outlook.com

---

<div align="center">

**If you find this project helpful, please consider giving it a ⭐ on GitHub!**

[⭐ Star on GitHub](https://github.com/realtuku/github-mng-bot)

</div>
