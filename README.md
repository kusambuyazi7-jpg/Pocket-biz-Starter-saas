# PocketBiz — Cloudflare-native full-stack MVP

This project uses HTML, CSS, vanilla JavaScript, Cloudflare Workers and D1 (SQLite). It avoids React, Node server hosting and build compilation for the browser assets.

## Included functionality
- Account registration/login, PBKDF2 password hashing, hashed random server sessions and secure HttpOnly cookies.
- Tenant-scoped business profile, products/services, customers, sales, sale items, expenses, payments, stock movements, dashboard summaries and JSON export.
- Credit sales require a customer; payment status and outstanding balances are reflected in dashboard summaries.
- Stock decreases when a product is sold; stock adjustment API is available.
- English/isiZulu starter UI, responsive mobile/desktop layout, ZAR amounts stored as integer cents.
- Cloudflare D1 schema and indexes; Worker security headers; parameterized SQL.

## Deploy
1. Install Node.js 20+ on a computer: https://nodejs.org
2. Extract this ZIP and open terminal in the folder.
3. Run `npm install`.
4. Run `npx wrangler login`.
5. Run `npx wrangler d1 create pocketbiz`; copy returned database ID into `wrangler.toml`.
6. Run `npx wrangler d1 migrations apply pocketbiz --remote`.
7. Run `npx wrangler deploy`.
8. Open the `workers.dev` URL, register an account, and test.

Local development: `npm run dev` (after D1 local migration: `npm run db:local`).

## Important honest limitations
This is a functional MVP foundation, not a fully production-certified commercial service. No automated WhatsApp sending, payment gateway checkout, email verification/password reset, multi-staff roles, recurring subscriptions, server-enforced rate limiting, advanced stock count UI, or full offline write queue is included. The frontend requires the Worker API; the standalone frontend ZIP is a UI-only package and cannot provide accounts or persistence when opened directly as a file. Do not enter real customer financial data until security, POPIA, backup/restore and recovery workflows are independently reviewed and tested.

## API
POST `/api/auth/register`, `/api/auth/login`, `/api/auth/logout`; GET/PUT `/api/business`; GET/POST `/api/products`, `/api/customers`, `/api/expenses`, `/api/payments`, `/api/stock-movements`, `/api/sales`; GET `/api/dashboard`, `/api/reports`, `/api/export`, `/api/health`.

Amounts in the API are integer cents, except user-facing form values which are converted from Rands.
