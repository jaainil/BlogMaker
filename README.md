# BlogMaker - Next.js Blog Creation Platform

A full-stack SaaS platform that allows users to create and manage their blogs easily.

## Tech Stack

- **Frontend**: Next.js 15 with App Router, React, TypeScript
- **Styling**: Tailwind CSS, Shadcn UI
- **Authentication**: Kinde Auth
- **Database**: PostgreSQL with Prisma ORM
- **Payment Processing**: Stripe
- **Image Storage**: UploadThing
- **Deployment**: Vercel

## Environment Variables

Create a `.env` file in the root directory with the following variables:

```env
# Database
DATABASE_URL="postgresql://..."
DIRECT_URL="postgresql://..."

# Authentication (Kinde)
KINDE_CLIENT_ID=""
KINDE_CLIENT_SECRET=""
KINDE_ISSUER_URL=""
KINDE_SITE_URL=""
KINDE_POST_LOGOUT_REDIRECT_URL=""
KINDE_POST_LOGIN_REDIRECT_URL=""

# Stripe
STRIPE_SECRET_KEY=""
STRIPE_WEBHOOK_SECRET=""
NEXT_PUBLIC_STRIPE_PUBLISHABLE_KEY=""

# uploadthing
UPLOADTHING_SECRET=""
UPLOADTHING_APP_ID=""
```

## Database Setup

This project uses Prisma ORM with PostgreSQL. Before running the application, you need to set up the database and run migrations.

### Prerequisites

1. Ensure you have a PostgreSQL database running
2. Update the `DATABASE_URL` and `DIRECT_URL` in your `.env` file with your database credentials

### Running Migrations

If you're setting up the project for the first time or encounter database-related errors (like "table does not exist"), follow these steps:

1. **Check if migrations exist**:

   ```bash
   ls prisma/migrations
   ```

2. **If no migrations exist, create the initial migration**:

   ```bash
   npx prisma migrate dev --name init
   ```

3. **Generate Prisma client**:

   ```bash
   npx prisma generate
   ```

4. **Verify database sync** (optional):
   ```bash
   npx prisma db push
   ```

### Common Database Issues

If you encounter errors like:

- `The table 'public.Site' does not exist in the current database`
- `PrismaClientKnownRequestError`

This typically means:

1. Your Prisma schema defines models that don't exist in the database yet
2. The `DIRECT_URL` environment variable might be missing from your `.env` file
3. Migrations haven't been run

**Solution**: Run the migration steps above to create all necessary tables including:

- `User`
- `Site`
- `Post`
- `Subscription`

## Getting Started

First, ensure your database is set up and migrations are run, then start the development server:

```bash
npm run dev
# or
yarn dev
# or
pnpm dev
# or
bun dev
```

Open [http://localhost:3000](http://localhost:3000) with your browser to see the result.

You can start editing the page by modifying `app/page.tsx`. The page auto-updates as you edit the file.

This project uses [`next/font`](https://nextjs.org/docs/app/building-your-application/optimizing/fonts) to automatically optimize and load Inter, a custom Google Font.

## Learn More

To learn more about Next.js, take a look at the following resources:

- [Next.js Documentation](https://nextjs.org/docs) - learn about Next.js features and API.
- [Learn Next.js](https://nextjs.org/learn) - an interactive Next.js tutorial.

You can check out [the Next.js GitHub repository](https://github.com/vercel/next.js) - your feedback and contributions are welcome!

## Deploy on Vercel

The easiest way to deploy your Next.js app is to use the [Vercel Platform](https://vercel.com/new?utm_medium=default-template&filter=next.js&utm_source=create-next-app&utm_campaign=create-next-app-readme) from the creators of Next.js.

Check out our [Next.js deployment documentation](https://nextjs.org/docs/app/building-your-application/deploying) for more details.
