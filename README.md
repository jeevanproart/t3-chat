# T3 Chat - AI-Powered Conversational Platform

A modern, full-stack AI chat application built with Next.js 15, featuring real-time conversations powered by multiple AI models, authentication, and persistent chat history.

## 🚀 Live Demo

[View Live Application](https://your-app.vercel.app) <!-- Update with your Vercel URL -->

## 📖 Overview

T3 Chat is a sophisticated conversational AI platform that enables users to interact with various AI models through an intuitive, responsive interface. Built with the latest web technologies, it provides seamless authentication, real-time messaging, and persistent chat storage.

## ✨ Key Features

- **🤖 Multi-Model AI Support** - Integrate with multiple AI models via OpenRouter API
- **🔐 Secure Authentication** - GitHub OAuth integration using Better Auth
- **💬 Real-time Chat** - Smooth, responsive chat interface with streaming responses
- **💾 Persistent Storage** - PostgreSQL database with Prisma ORM for chat history
- **🎨 Modern UI/UX** - Beautiful, responsive design with Radix UI components
- **⚡ High Performance** - Built with Next.js 15 and Turbopack for optimal speed
- **🌙 Dark Mode** - Theme switching support with next-themes
- **📱 Responsive Design** - Fully responsive across desktop, tablet, and mobile devices

## 🛠️ Tech Stack

### Frontend
- **Framework**: Next.js 15.5.4 (React 19)
- **Build Tool**: Turbopack
- **Styling**: Tailwind CSS 4
- **UI Components**: Radix UI
- **State Management**: Zustand
- **Data Fetching**: TanStack Query (React Query)
- **AI Integration**: Vercel AI SDK

### Backend
- **Runtime**: Node.js
- **API Routes**: Next.js App Router API Routes
- **Authentication**: Better Auth with GitHub OAuth
- **Database**: PostgreSQL
- **ORM**: Prisma
- **AI Provider**: OpenRouter

### DevOps
- **Deployment**: Vercel
- **Database Hosting**: Neon (Serverless PostgreSQL)
- **Version Control**: Git & GitHub
- **Container**: Docker (for local database)

## 📦 Project Structure

```
t3-chat/
├── src/
│   ├── app/                    # Next.js app router pages
│   │   ├── (auth)/            # Authentication pages
│   │   ├── (root)/            # Main application pages
│   │   └── api/               # API routes
│   ├── components/
│   │   ├── ai-elements/       # AI-specific components
│   │   ├── ui/                # Reusable UI components
│   │   └── providers/         # Context providers
│   ├── modules/
│   │   ├── authentication/    # Auth logic and components
│   │   ├── chat/             # Chat functionality
│   │   └── messages/         # Message handling
│   ├── lib/                   # Utility functions
│   └── hooks/                 # Custom React hooks
├── prisma/
│   ├── schema.prisma         # Database schema
│   └── migrations/           # Database migrations
├── public/                    # Static assets
└── docker-compose.yml        # Local database setup
```

## 🚀 Getting Started

### Prerequisites

- Node.js 18+ or later
- Docker Desktop (for local database)
- GitHub account (for authentication)
- OpenRouter API key

### Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/jeevanproart/t3-chat.git
   cd t3-chat
   ```

2. **Install dependencies**
   ```bash
   pnpm install
   # or
   npm install
   ```

3. **Set up environment variables**
   
   Create a `.env` file in the root directory:
   ```env
   DATABASE_URL="postgresql://postgres:postgres@localhost:5430/postgres"
   OPENROUTER_API_KEY="your_openrouter_api_key"
   GITHUB_CLIENT_ID="your_github_client_id"
   GITHUB_CLIENT_SECRET="your_github_client_secret"
   BETTER_AUTH_SECRET="your_random_secret"
   BETTER_AUTH_URL="http://localhost:3000"
   ```

4. **Start Docker database**
   ```bash
   docker compose up -d
   ```

5. **Run database migrations**
   ```bash
   pnpm prisma migrate deploy
   ```

6. **Start development server**
   ```bash
   pnpm dev
   ```

7. **Open your browser**
   
   Navigate to [http://localhost:3000](http://localhost:3000)

## 📝 Environment Variables

| Variable | Description | Required |
|----------|-------------|----------|
| `DATABASE_URL` | PostgreSQL connection string | Yes |
| `OPENROUTER_API_KEY` | API key from OpenRouter | Yes |
| `GITHUB_CLIENT_ID` | GitHub OAuth app client ID | Yes |
| `GITHUB_CLIENT_SECRET` | GitHub OAuth app secret | Yes |
| `BETTER_AUTH_SECRET` | Random secret for auth | Yes |
| `BETTER_AUTH_URL` | Application base URL | Yes |

## 🗄️ Database Schema

The application uses PostgreSQL with the following main entities:

- **User** - User accounts and profiles
- **Session** - User sessions for authentication
- **Account** - OAuth account linkage
- **Chat** - Individual chat conversations
- **Message** - Chat messages with role and type
- **Verification** - Email/auth verification tokens

## 🌐 Deployment

The application is production-ready and can be deployed to Vercel:

1. Push code to GitHub
2. Import project in Vercel
3. Add environment variables
4. Deploy

For detailed deployment instructions, see [DEPLOYMENT.md](./DEPLOYMENT.md)

## 🔒 Authentication Flow

1. User clicks "Sign in with GitHub"
2. Redirect to GitHub OAuth authorization
3. GitHub callback with authorization code
4. Better Auth validates and creates session
5. User redirected to application dashboard

## 🤝 Contributing

Contributions, issues, and feature requests are welcome!

## 📄 License

This project is open source and available under the [MIT License](LICENSE).

## 👤 Author

**Jeevan**
- GitHub: [@jeevanproart](https://github.com/jeevanproart)

## 🙏 Acknowledgments

- [Next.js](https://nextjs.org/) - React framework
- [OpenRouter](https://openrouter.ai/) - AI model API
- [Vercel](https://vercel.com/) - Deployment platform
- [Neon](https://neon.tech/) - Serverless PostgreSQL
- [Better Auth](https://better-auth.com/) - Authentication library
- [Radix UI](https://www.radix-ui.com/) - UI components
- [Prisma](https://www.prisma.io/) - Database ORM

---

**Built with ❤️ using modern web technologies**
