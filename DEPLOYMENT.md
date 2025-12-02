# Deployment Guide - Vercel + Neon DB

This guide will walk you through deploying your T3 Chat application to Vercel with a Neon PostgreSQL database.

## Prerequisites

- GitHub account
- Vercel account (sign up at https://vercel.com - use GitHub to sign in)
- Neon account (sign up at https://neon.tech - use GitHub to sign in)

## Step 1: Create Neon PostgreSQL Database

1. **Go to Neon Dashboard**
   - Visit: https://console.neon.tech
   - Sign in with GitHub

2. **Create New Project**
   - Click "Create Project" or "New Project"
   - Project Name: `t3-chat-db` (or any name you prefer)
   - Region: Choose closest to your users
   - PostgreSQL Version: 16 (or latest stable)
   - Click "Create Project"

3. **Get Database Connection String**
   - After creation, you'll see a connection string like:
   ```
   postgresql://username:password@ep-xxx-xxx.region.aws.neon.tech/neondb?sslmode=require
   ```
   - **SAVE THIS** - you'll need it for Vercel environment variables

## Step 2: Push Code to GitHub

Your code needs to be on GitHub for Vercel to deploy it.

1. **Create a new repository on GitHub**
   - Go to https://github.com/new
   - Repository name: `t3-chat` (or any name)
   - Make it Private or Public (your choice)
   - **Do NOT** initialize with README (your project already has one)
   - Click "Create repository"

2. **Push your local code to GitHub**
   ```bash
   # These commands will be run for you
   git add .
   git commit -m "Initial commit - ready for deployment"
   git branch -M main
   git remote add origin https://github.com/YOUR_USERNAME/REPO_NAME.git
   git push -u origin main
   ```

## Step 3: Deploy to Vercel

1. **Go to Vercel Dashboard**
   - Visit: https://vercel.com/dashboard
   - Sign in with GitHub

2. **Import Project**
   - Click "Add New..." → "Project"
   - Select your GitHub repository (`t3-chat`)
   - Click "Import"

3. **Configure Project**
   - Framework Preset: Next.js (should auto-detect)
   - Root Directory: `./` (leave as is)
   - **Do NOT click Deploy yet!**

4. **Add Environment Variables**
   Click "Environment Variables" and add these:

   ```
   DATABASE_URL = postgresql://your-neon-connection-string-here
   OPENROUTER_API_KEY = your_openrouter_api_key
   GITHUB_CLIENT_ID = Ov23liG96LttBud3yMhK
   GITHUB_CLIENT_SECRET = your_github_client_secret
   BETTER_AUTH_SECRET = 4GNtfPkIrpHBT1lpFASBvDMjLN2WCN5YOpICPX345Eg=
   BETTER_AUTH_URL = https://your-app-name.vercel.app
   NODE_ENV = production
   ```

   **Note:** For `BETTER_AUTH_URL`, you can use the Vercel project name first (e.g., `t3-chat-username.vercel.app`), or you can edit it after deployment.

5. **Click "Deploy"**
   - Vercel will build and deploy your app
   - This takes 2-3 minutes

## Step 4: Run Database Migrations

After deployment completes:

1. **Install Vercel CLI** (if not already installed)
   ```bash
   npm i -g vercel
   ```

2. **Login to Vercel**
   ```bash
   vercel login
   ```

3. **Link to your project**
   ```bash
   cd /Users/jeevan/Downloads/t3-chat-master
   vercel link
   ```

4. **Run migrations on production database**
   ```bash
   vercel env pull .env.production
   DATABASE_URL="your-neon-connection-string" npx prisma migrate deploy
   ```

## Step 5: Update GitHub OAuth App

1. **Go to GitHub OAuth app settings**
   - Visit: https://github.com/settings/developers
   - Click on your OAuth app

2. **Add Production Callback URL**
   - In "Authorization callback URL" section
   - Add: `https://your-app-name.vercel.app/api/auth/callback/github`
   - Click "Update application"

## Step 6: Test Your Deployment

1. Visit your Vercel URL: `https://your-app-name.vercel.app`
2. Click "Sign in with GitHub"
3. Create a new chat
4. Verify everything works!

## Troubleshooting

### Database connection errors
- Verify DATABASE_URL in Vercel environment variables
- Ensure migrations were run successfully

### GitHub OAuth errors
- Verify callback URL is correct
- Check GITHUB_CLIENT_ID and GITHUB_CLIENT_SECRET

### Build failures
- Check Vercel build logs
- Ensure all dependencies are in package.json

## Environment Variables Reference

| Variable | Where to Find |
|----------|--------------|
| DATABASE_URL | Neon dashboard → Connection string |
| OPENROUTER_API_KEY | OpenRouter dashboard |
| GITHUB_CLIENT_ID | GitHub OAuth app settings |
| GITHUB_CLIENT_SECRET | GitHub OAuth app settings |
| BETTER_AUTH_SECRET | Generated with `openssl rand -base64 32` |
| BETTER_AUTH_URL | Your Vercel deployment URL |

---

**Need help?** Let me know if you encounter any issues during deployment!
