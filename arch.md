# BnB Booking Website - Architecture & Design Plan

## 1. System Overview

### Core Features
- **Guest Booking System**: Search, filter, and book properties
- **Owner Admin Panel**: Manage property details, pricing, availability, and activities
- **Calendar Management**: Block dates, set minimum stays, manage rates
- **Payment Processing**: Secure payment handling via Stripe
- **Real-time Updates**: Live availability and booking status

---

## 2. Technology Stack

### Frontend Architecture
- **Framework**: Next.js 14 (React + Server Components)
- **Language**: TypeScript
- **State Management**: TanStack Query (React Query) + Zustand
- **Styling**: Tailwind CSS + Shadcn/ui
- **Maps**: Mapbox GL JS
- **Form Handling**: React Hook Form + Zod validation
- **Date Handling**: date-fns or Day.js
- **Hosting**: Vercel

### Backend Architecture
- **Runtime**: Node.js 20+
- **Framework**: NestJS (TypeScript)
- **API Style**: REST + WebSocket (Socket.io)
- **Validation**: class-validator, Joi
- **File Upload**: Multer + AWS SDK
- **Authentication**: Passport.js (JWT, OAuth)
- **Rate Limiting**: express-rate-limit
- **Logging**: Winston / Pino
- **Testing**: Jest, Supertest

### Database Architecture
- **Primary**: PostgreSQL 15+
  - Tables: users, properties, bookings, calendar_blocks, reviews, activities
  - ORM: Prisma
  - Migrations: Prisma Migrate
- **Cache**: Redis 7+
  - Sessions, availability checks, frequently accessed data
- **Search**: Elasticsearch 8+ (optional for v2)
  - Full-text search on properties, activities, reviews

### External Services
- **Payments**: Stripe API
- **Email**: SendGrid
- **SMS**: Twilio
- **File Storage**: AWS S3
- **Maps**: Mapbox
- **Analytics**: Google Analytics 4
- **Monitoring**: Sentry + DataDog

---

## 3. Database Schema

### Key Tables

#### Users
```sql
CREATE TABLE users (
  id UUID PRIMARY KEY DEFAULT uuid_generate_v4(),
  email VARCHAR(255) UNIQUE NOT NULL,
  password_hash VARCHAR(255),
  first_name VARCHAR(100),
  last_name VARCHAR(100),
  role ENUM('guest', 'owner', 'admin'),
  profile_image_url TEXT,
  phone VARCHAR(20),
  created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
  updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
