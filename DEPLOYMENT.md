# Kosi Digital - Deployment Guide

## Deploying to Vercel

This guide walks you through deploying Kosi Digital to Vercel with GitHub integration.

### Prerequisites

1. **GitHub Account** - Create one at https://github.com if you don't have one
2. **Vercel Account** - Sign up at https://vercel.com (free tier available)
3. **Environment Variables** - Gather all required secrets from your Manus project

### Step 1: Push to GitHub

1. Create a new repository on GitHub (e.g., `kosi-digital`)
2. In your local project directory, initialize git:

```bash
git init
git add .
git commit -m "Initial commit: Kosi Digital website"
git branch -M main
git remote add origin https://github.com/YOUR_USERNAME/kosi-digital.git
git push -u origin main
```

### Step 2: Connect to Vercel

1. Go to https://vercel.com/new
2. Click "Import Git Repository"
3. Select your GitHub repository (`kosi-digital`)
4. Vercel will auto-detect the project as a Vite + Node.js app

### Step 3: Configure Environment Variables

In the Vercel dashboard, add these environment variables under "Environment Variables":

**Required for OAuth & Auth:**
- `VITE_APP_ID` - From your Manus project
- `OAUTH_SERVER_URL` - Usually `https://api.manus.im`
- `VITE_OAUTH_PORTAL_URL` - From your Manus project
- `JWT_SECRET` - From your Manus project
- `OWNER_OPEN_ID` - Your Manus user ID
- `OWNER_NAME` - Your name

**Required for Database:**
- `DATABASE_URL` - Your MySQL connection string (e.g., from PlanetScale, AWS RDS, or Supabase)

**Required for Manus APIs:**
- `BUILT_IN_FORGE_API_URL` - From your Manus project
- `BUILT_IN_FORGE_API_KEY` - From your Manus project
- `VITE_FRONTEND_FORGE_API_KEY` - From your Manus project
- `VITE_FRONTEND_FORGE_API_URL` - From your Manus project

**Analytics (Optional):**
- `VITE_ANALYTICS_ENDPOINT` - Your analytics endpoint
- `VITE_ANALYTICS_WEBSITE_ID` - Your analytics website ID

### Step 4: Deploy

1. Click "Deploy" in the Vercel dashboard
2. Vercel will build and deploy your project
3. Your site will be live at `https://your-project.vercel.app`

### Step 5: Custom Domain (Optional)

1. In Vercel dashboard, go to "Settings" → "Domains"
2. Add your custom domain (e.g., `kosidigital.com`)
3. Follow the DNS configuration instructions

### Troubleshooting

**Build Fails:**
- Check that all environment variables are set correctly
- Ensure `DATABASE_URL` is valid and accessible from Vercel
- Check build logs in Vercel dashboard for specific errors

**Database Connection Issues:**
- Verify `DATABASE_URL` format: `mysql://user:password@host:port/database`
- Ensure your database allows connections from Vercel IPs
- For PlanetScale: Enable "Allow any IPv4 address" in connection settings

**OAuth Not Working:**
- Verify `VITE_APP_ID` and `OAUTH_SERVER_URL` are correct
- Check that your Manus project allows the Vercel domain as a redirect URI

### Updating Your Site

After deployment, any changes you push to GitHub will automatically trigger a new deployment:

```bash
git add .
git commit -m "Update: Add new feature"
git push origin main
```

Vercel will automatically rebuild and redeploy your site.

### Database Migrations

If you update your database schema:

1. Generate migrations locally: `pnpm db:push`
2. Push changes to GitHub
3. After Vercel deploys, run migrations on your production database

For automated migrations on deploy, consider using a Vercel Function or webhook.

### Monitoring

- **Vercel Dashboard** - Monitor deployments, analytics, and errors
- **Database Logs** - Check your database provider's logs for connection issues
- **Error Tracking** - Set up Sentry or similar for production error monitoring

---

## Alternative: Deploy on Your Own Server

If you prefer not to use Vercel, you can deploy to:
- **Railway** - `railway.app`
- **Render** - `render.com`
- **Fly.io** - `fly.io`
- **Your own VPS** - DigitalOcean, Linode, AWS EC2

Contact support if you need help with alternative hosting options.
