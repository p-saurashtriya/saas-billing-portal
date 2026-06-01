# BillingOS — The Future of SaaS Billing Infrastructure

## Overview

BillingOS is a production-grade SaaS Billing Platform built with the MERN stack, featuring intelligent subscription management, secure authentication, invoice automation, analytics dashboards, and enterprise-grade role-based access control.

## Features

### User Roles
- **superadmin** - Full system access, user role assignment, plan deletion
- **admin** - Dashboard analytics, user management, plan CRUD, all invoices
- **billing_manager** - View subscriptions, manage invoices, mark paid
- **user** - Dashboard, subscribe to plans, view own invoices, profile

### Core Modules
- 🔐 **Auth** — Register, Login, JWT, Change Password, Profile Update
- 💳 **Plans** — Tiered pricing (Starter / Pro / Business), monthly & yearly billing
- 📦 **Subscriptions** — Subscribe, Upgrade, Cancel, auto-generated invoices
- 🧾 **Invoices** — Detailed invoice with line items, tax (18%), status tracking
- 📊 **Admin Dashboard** — Revenue bar chart, subscription doughnut chart, stat cards
- 👥 **User Management** — Search, filter by role, activate/deactivate, role assignment
- 🎨 **Premium UI** — Dark theme, Sora font, smooth gradients, responsive layout

## Tech Stack

**Frontend:** React 18, React Router v6, Bootstrap 5, Chart.js, Axios, React Toastify  
**Backend:** Node.js, Express.js, MongoDB, Mongoose, JWT, bcryptjs  
**Dev Tools:** Nodemon, dotenv

## Installation & Setup

### Prerequisites
- Node.js v18+
- MongoDB (local or MongoDB Atlas)
- Git

### Setup

```bash
# Backend
cd backend
npm install
cp .env.example .env
npm run seed
npm run dev

# Frontend (new terminal)
cd frontend
npm install
cp .env.example .env
npm start
```

## Demo Credentials

| Role | Email | Password |
|---|---|---|
| Super Admin | superadmin@billing.dev | Admin@1234 |
| Admin | admin@billing.dev | Admin@1234 |
| Billing Manager | billing@billing.dev | Admin@1234 |
| User (Pro) | gyana@example.com | User@1234 |
| User (Business) | priya@example.com | User@1234 |

## API Documentation

### Auth
- `POST /api/auth/register` - Register account
- `POST /api/auth/login` - Login, get JWT
- `GET /api/auth/me` - Get current user
- `PUT /api/auth/profile` - Update profile
- `PUT /api/auth/change-password` - Change password

### Plans
- `GET /api/plans` - List all active plans
- `POST /api/plans` - Create plan (Admin)
- `PUT /api/plans/:id` - Update plan (Admin)
- `DELETE /api/plans/:id` - Deactivate plan (Superadmin)

### Subscriptions
- `POST /api/subscriptions` - Subscribe to plan
- `GET /api/subscriptions/my` - Get my subscription
- `PUT /api/subscriptions/upgrade` - Upgrade/change plan
- `PUT /api/subscriptions/cancel` - Cancel subscription
- `GET /api/subscriptions` - All subscriptions (Admin/BM)

### Invoices
- `GET /api/invoices/my` - My invoices
- `GET /api/invoices/:id` - Invoice detail
- `GET /api/invoices` - All invoices (Admin/BM)
- `PUT /api/invoices/:id/mark-paid` - Mark as paid (Admin/BM)

### Admin
- `GET /api/admin/stats` - Dashboard analytics
- `GET /api/admin/users` - List users
- `PUT /api/admin/users/:id/role` - Change user role (Superadmin)
- `PUT /api/admin/users/:id/toggle-active` - Activate/Deactivate

## Environment Variables

### Backend `.env`
```
PORT=5000
NODE_ENV=development
MONGO_URI=mongodb://localhost:27017/saas_billing_portal
JWT_SECRET=your_super_secret_jwt_key_here_change_in_production
JWT_EXPIRE=7d
CLIENT_URL=http://localhost:3000
```

### Frontend `.env`
```
REACT_APP_API_URL=http://localhost:5000/api
```

## Deployment

1. Build frontend: `cd frontend && npm run build`
2. Deploy backend to Render/Railway
3. Deploy frontend to Vercel/Netlify
4. Set `NODE_ENV=production` and use MongoDB Atlas
5. Configure CORS `CLIENT_URL` to production domain

## License

MIT
