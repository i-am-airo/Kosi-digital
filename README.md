# Kosi Digital - Ad Creative & Lead Generation for Real Estate

A professional web application for real estate agents to manage ad creatives, video editing, campaign management, and lead generation.

## Features

- **Ad Creative Management** - Create and manage static and video ad creatives
- **Campaign Management** - Set up and monitor Meta Ads campaigns
- **Lead Generation** - Capture and track qualified leads
- **Landing Page Setup** - Build high-converting landing pages
- **AI Automation** - Automate follow-ups and lead nurturing
- **Email Subscriptions** - Build your newsletter audience
- **Real-time Analytics** - Track campaign performance

## Tech Stack

- **Frontend**: React 19 + Tailwind CSS 4 + Vite
- **Backend**: Express 4 + tRPC 11
- **Database**: MySQL (Drizzle ORM)
- **Auth**: Manus OAuth
- **Deployment**: Vercel

## Getting Started

### Prerequisites

- Node.js 22+
- pnpm 10+
- MySQL database

### Installation

1. Clone the repository:
```bash
git clone https://github.com/YOUR_USERNAME/kosi-digital.git
cd kosi-digital
```

2. Install dependencies:
```bash
pnpm install
```

3. Set up environment variables:
```bash
cp .env.example .env.local
# Edit .env.local with your configuration
```

4. Initialize the database:
```bash
pnpm db:push
```

5. Start the development server:
```bash
pnpm dev
```

Visit `http://localhost:3000` to see your app.

## Project Structure

```
kosi-digital/
├── client/                 # React frontend
│   ├── src/
│   │   ├── components/    # Reusable UI components
│   │   ├── pages/         # Page components
│   │   ├── lib/           # Utilities and helpers
│   │   └── App.tsx        # Main app component
│   └── index.html
├── server/                 # Express backend
│   ├── db.ts              # Database queries
│   ├── routers.ts         # tRPC procedures
│   └── _core/             # Core server setup
├── drizzle/               # Database schema & migrations
├── shared/                # Shared types and constants
├── vercel.json            # Vercel configuration
└── package.json
```

## Development

### Running Tests

```bash
pnpm test
```

### Type Checking

```bash
pnpm check
```

### Building for Production

```bash
pnpm build
```

### Database Migrations

After updating the schema in `drizzle/schema.ts`:

```bash
pnpm db:push
```

## Deployment

### Deploy to Vercel

See [DEPLOYMENT.md](./DEPLOYMENT.md) for detailed instructions.

Quick start:
1. Push to GitHub
2. Connect repository to Vercel
3. Add environment variables
4. Deploy

### Environment Variables

Required for production:
- `DATABASE_URL` - MySQL connection string
- `JWT_SECRET` - Session signing secret
- `VITE_APP_ID` - OAuth app ID
- `OAUTH_SERVER_URL` - OAuth server URL
- `VITE_OAUTH_PORTAL_URL` - OAuth portal URL
- `OWNER_OPEN_ID` - Owner's user ID
- `OWNER_NAME` - Owner's name
- `BUILT_IN_FORGE_API_URL` - Manus API URL
- `BUILT_IN_FORGE_API_KEY` - Manus API key
- `VITE_FRONTEND_FORGE_API_KEY` - Frontend API key
- `VITE_FRONTEND_FORGE_API_URL` - Frontend API URL

## API Documentation

### Newsletter Subscription

**Endpoint**: `POST /api/trpc/newsletter.subscribe`

**Input**:
```json
{
  "email": "agent@example.com",
  "name": "John Doe",
  "source": "blog_newsletter"
}
```

**Response**:
```json
{
  "success": true,
  "message": "Successfully subscribed to our newsletter!"
}
```

## Database Schema

### email_subscriptions
- `id` - Primary key
- `email` - Subscriber email (unique)
- `name` - Subscriber name (optional)
- `source` - Subscription source (blog_newsletter, contact_form)
- `status` - Subscription status (subscribed, unsubscribed)
- `createdAt` - Subscription date
- `updatedAt` - Last update date

### users
- `id` - Primary key
- `openId` - Manus OAuth ID (unique)
- `name` - User name
- `email` - User email
- `loginMethod` - Login method
- `role` - User role (user, admin)
- `createdAt` - Account creation date
- `updatedAt` - Last update date
- `lastSignedIn` - Last login date

## Contributing

1. Create a feature branch: `git checkout -b feature/your-feature`
2. Commit changes: `git commit -m "Add your feature"`
3. Push to branch: `git push origin feature/your-feature`
4. Open a pull request

## Support

For issues and questions:
- Check existing GitHub issues
- Create a new issue with detailed description
- Contact: kosidigitalm@gmail.com
- WhatsApp: +234 805 127 6247

## License

MIT License - see LICENSE file for details

## Roadmap

- [ ] Advanced analytics dashboard
- [ ] AI-powered creative suggestions
- [ ] Multi-language support
- [ ] Mobile app
- [ ] Zapier integration
- [ ] Slack notifications

---

**Made with ❤️ by Kosi Digital**
