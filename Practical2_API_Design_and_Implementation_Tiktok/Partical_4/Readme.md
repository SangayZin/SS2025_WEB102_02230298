#  Practical 4: Connecting TikTok to PostgreSQL with Prisma ORM

##  Objectives
- Set up a PostgreSQL database for a TikTok clone application
- Configure Prisma ORM for database access
- Replace in-memory data models with persistent storage
- Implement secure authentication with password encryption
- Update RESTful API endpoints to work with the database

---

##  Part 1: Setting Up PostgreSQL Database

###  Step 1: Create the Database

**Open PostgreSQL CLI:**
```bash
sudo -u postgres psql
```

**Run SQL commands:**
```sql
CREATE DATABASE tiktok_db;
CREATE USER tiktok_user WITH ENCRYPTED PASSWORD 'your_password';
GRANT ALL PRIVILEGES ON DATABASE tiktok_db TO tiktok_user;
```

**Exit:**
```bash
\q
```

---

## ⚙️ Part 2: Setting Up Prisma ORM

###  Step 1: Install Prisma Dependencies
```bash
cd server
npm install @prisma/client
npm install prisma --save-dev
```

###  Step 2: Initialize Prisma
```bash
npx prisma init
```

This creates:
- `prisma/schema.prisma`
- `.env` file for environment variables

###  Step 3: Configure Database Connection

In `.env`:
```env
DATABASE_URL="postgresql://tiktok_user:your_password@localhost:5432/tiktok_db?schema=public"
```

### Step 4: Install Extra Dependencies
```bash
npm install bcrypt jsonwebtoken
```

---

##  Part 3: Creating Database Schema

###  Step 1: Create Initial Migration
```bash
npx prisma migrate dev --name init
```

This:
- Generates SQL migration files
- Applies them to the database
- Generates Prisma Client

### Step 2: Prisma Client Setup

Create `src/lib/prisma.js`:
```javascript
const { PrismaClient } = require('@prisma/client');
const prisma = new PrismaClient();
module.exports = prisma;
```

###  Step 3: Create Authentication Middleware

Create `src/middleware/auth.js` for verifying JWT tokens.

---

##  Part 4: Updating Controllers to Use Prisma

###  User Controller
- Password hashing using bcrypt
- JWT token creation with jsonwebtoken
- Prisma for DB queries

###  Video Controller
- Relational data fetching
- Transactions

###  Comment Controller
- Create/read/delete comments with Prisma

---

##  Part 5: Authentication Implementation

###  Protected Routes
- Create JWT auth middleware
- Apply middleware to protected endpoints

### ⚙️ Environment Variables
```env
PORT=5000
NODE_ENV=development
DATABASE_URL="postgresql://tiktok_user:your_password@localhost:5432/tiktok_db?schema=public"
JWT_SECRET=yourverylongandsecurerandomsecret
JWT_EXPIRE=30d
```

---

##  Part 6: Testing Integration

###  Start Server
```bash
npm run dev
```

###  Use Postman to Test:
-  Register User
-  Login User
-  Access Protected Routes with JWT
-  Upload/Create Video

---

## Part 7: Creating Test Data

###  Seed File: `prisma/seed.js`

Populate DB with:
-  10 Users
-  50 Videos (5 per user)
-  200 Comments
-  300 Video Likes
-  150 Comment Likes
-  40 Follow Relationships

###  Add Seed Script in `package.json`
```json
"scripts": {
  "dev": "nodemon src/index.js",
  "start": "node src/index.js",
  "seed": "node prisma/seed.js"
}
```

###  Run Seed Script
```bash
npm run seed
```

---

##  Key Concepts Summary

### Database Design
- Tables represent entities
- Foreign keys maintain integrity
- Indexes improve query performance
- Relationships (1:M, M:M)

###  ORM (Prisma)
- Maps models to DB tables
- Type-safe queries
- Simplified migration process

###  Authentication & Security
- Passwords hashed with bcrypt
- JWT for secure stateless auth
- Middleware to protect routes

###  Prisma Features
- Schema-first model definitions
- Database migrations
- Relationship support
- Transaction handling

---

##  Resources
- Prisma Documentation
- PostgreSQL Documentation
- JWT Authentication Guide
- Postman API Testing Guide

---

##  Getting Started

1. Clone the repo
2. Install dependencies:
```bash
npm install
```
3. Set up PostgreSQL DB
4. Configure `.env` file
5. Run migrations:
```bash
npx prisma migrate dev
```
6. Seed database:
```bash
npm run seed
```
7. Start server:
```bash
npm run dev
```