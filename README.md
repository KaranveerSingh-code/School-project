# Bharat Voyager

An all-in-one travel platform built with Next.js 15, TypeScript, Tailwind CSS, and Supabase.

## Features

### Authentication
- User registration
- Login/logout
- Password reset
- Protected routes
- Profile management

### Dashboard
- Upcoming trips
- Recent bookings
- Budget overview
- Travel statistics
- Quick actions

### Trip Planner
- Create trips
- Manage itineraries
- Daily activities
- Destination notes
- Travel checklist

### Hotel Management
- Browse hotels
- Hotel details
- Favorites/Wishlist
- Booking management
- Reviews and ratings

### Flight Search
- Search flights
- Departure and arrival filters
- Airline filters
- Flight comparison
- Save flights

### Budget Tracker
- Trip budgets
- Expense tracking
- Spending categories
- Budget alerts
- Reports and charts

### AI Itinerary Generator
- Destination-based plans
- Budget-aware recommendations
- Daily schedules
- Attractions suggestions
- Food recommendations

---

# Tech Stack

## Frontend

- Next.js 15
- TypeScript
- Tailwind CSS
- Shadcn UI
- React Hook Form
- Zod

## Backend

- Supabase
- PostgreSQL
- Edge Functions

## AI

- OpenAI API

## Deployment

- Vercel
- Supabase

---

# Folder Structure

```txt
bharat-voyager/
│
├── app/
│   ├── (auth)/
│   │   ├── login/
│   │   ├── register/
│   │   └── forgot-password/
│   │
│   ├── dashboard/
│   ├── trips/
│   ├── hotels/
│   ├── flights/
│   ├── budget/
│   ├── ai-planner/
│   ├── profile/
│   ├── api/
│   ├── layout.tsx
│   └── page.tsx
│
├── components/
│   ├── dashboard/
│   ├── trips/
│   ├── hotels/
│   ├── flights/
│   ├── budget/
│   ├── ai/
│   └── shared/
│
├── lib/
│   ├── supabase/
│   ├── auth/
│   ├── ai/
│   └── utils/
│
├── services/
│   ├── flight-service.ts
│   ├── hotel-service.ts
│   ├── budget-service.ts
│   └── ai-service.ts
│
├── public/
│
├── types/
│
├── supabase/
│   ├── migrations/
│   └── seed.sql
│
├── package.json
├── next.config.ts
├── tailwind.config.ts
├── tsconfig.json
├── middleware.ts
└── README.md
```

---

# Installation

## Clone Repository

```bash
git clone https://github.com/yourusername/bharat-voyager.git

cd bharat-voyager
```

## Install Dependencies

```bash
npm install
```

## Environment Variables

Create a `.env.local` file.

```env
NEXT_PUBLIC_SUPABASE_URL=
NEXT_PUBLIC_SUPABASE_ANON_KEY=
SUPABASE_SERVICE_ROLE_KEY=

OPENAI_API_KEY=

NEXT_PUBLIC_APP_URL=http://localhost:3000
```

---

# Supabase Setup

Create a new Supabase project.

Run database migrations:

```bash
npx supabase db push
```

Start local Supabase:

```bash
npx supabase start
```

---

# Run Development Server

```bash
npm run dev
```

Open:

```txt
http://localhost:3000
```

---

# Database Schema

## Users

```sql
create table profiles (
  id uuid primary key references auth.users(id),
  full_name text,
  avatar_url text,
  created_at timestamptz default now()
);
```

## Trips

```sql
create table trips (
  id uuid primary key default gen_random_uuid(),
  user_id uuid references profiles(id),
  title text,
  destination text,
  start_date date,
  end_date date,
  budget numeric,
  created_at timestamptz default now()
);
```

## Hotels

```sql
create table hotels (
  id uuid primary key default gen_random_uuid(),
  name text,
  city text,
  country text,
  description text,
  rating numeric,
  image_url text
);
```

## Flights

```sql
create table flights (
  id uuid primary key default gen_random_uuid(),
  airline text,
  flight_number text,
  departure_city text,
  arrival_city text,
  departure_time timestamptz,
  arrival_time timestamptz
);
```

## Expenses

```sql
create table expenses (
  id uuid primary key default gen_random_uuid(),
  trip_id uuid references trips(id),
  category text,
  amount numeric,
  note text,
  created_at timestamptz default now()
);
```

---

# Deployment

## Deploy Frontend

```bash
vercel
```

## Deploy Supabase

Use hosted Supabase project.

---

# Build

```bash
npm run build
```

---

# Production

```bash
npm run start
```

---

# Future Enhancements

- Real-time flight APIs
- Booking.com integration
- Google Maps integration
- Travel insurance
- Visa assistant
- Group travel planning
- Mobile application
- Offline mode
- Multi-language support

---

# License

MIT License

Copyright (c) 2026 Bharat Voyager

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software.
