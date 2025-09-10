# 🎉 Groupie

**Groupie** is your crew’s AI-powered planner — turning messy group chats into clear, fun plans with polls, invites, RSVPs, and reminders.  

---

## ✨ Features (MVP)
- 📲 **Bot-first**: Kick off plans from SMS (Twilio), WhatsApp, or chat exports
- 🗳 **Polls**: Auto-generate 2–3 venue/time options, tap-to-vote links
- 🔒 **Lock**: Automatically confirm once deadline/quorum hits
- 📅 **Invites**: Mobile-friendly pages with map links + “Add to Calendar”
- 🔔 **Reminders**: Day-of nudges so no one flakes

---

## 🛠️ Tech Stack
- **Web**: Next.js + Tailwind (invite & poll pages)
- **Bot**: Node.js + Express (Twilio/WhatsApp webhook)
- **Database**: Supabase/Postgres
- **Infra**: Vercel (web), ngrok (local bot testing)
- **APIs**: Google Places (venues), Splitwise (optional cost-splitting)

---

## 📦 Monorepo Layout

```
groupie/
├─ apps/
│  ├─ web/        # Next.js app (polls, invites, host console)
│  └─ bot/        # Node/TS bot (Twilio/WhatsApp webhook)
├─ packages/
│  ├─ db/         # Supabase client, migrations, schema
│  ├─ shared/     # types, zod schemas, constants, copy
│  └─ config/     # tsconfig, eslint, prettier, tailwind presets
├─ infra/         # (optional) deployment + infra notes
└─ README.md
```

---

## 🚀 Getting Started

### 1. Clone & Install
```bash
git clone https://github.com/alecdalelio/groupie.git
cd groupie
pnpm install
```

### 2. Environment Variables

Copy .env.example → .env and fill in:
```
SUPABASE_URL=
SUPABASE_ANON_KEY=
SUPABASE_SERVICE_ROLE_KEY=

TWILIO_ACCOUNT_SID=
TWILIO_AUTH_TOKEN=
TWILIO_MESSAGING_SERVICE_SID=
PUBLIC_BASE_URL=http://localhost:3000

NEXT_PUBLIC_SUPABASE_URL=
NEXT_PUBLIC_SUPABASE_ANON_KEY=
```

### 3. Database Setup

Run migrations:
```
supabase db push
```

### 4. Run Dev
```
pnpm dev   # runs both web + bot via turborepo
```

### 5. Expose Bot Locally
```
ngrok http 3001
# Paste your ngrok URL into Twilio webhook settings
```
