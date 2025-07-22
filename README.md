# Invoice Management System

This is a full-stack Invoice Management System designed to help businesses manage their invoices, customers, and payments efficiently. It features a React-based frontend and a Node.js Express backend, with integrated Stripe functionalities for subscriptions, payments, and payouts.

## Project Structure

This project is organized as a monorepo, containing two main applications:

-   `invoice-management-client/`: The frontend React application.
-   `invoice-management-server/`: The backend Node.js Express API.

## Features

### Frontend

*   User Authentication (Vendor & Admin roles)
*   Customer Management (Add, View)
*   Invoice Creation and Management
*   Stripe Integration for saving card details and charging customers
*   Subscription Management
*   Payout Request and History
*   Admin Dashboard for vendor approval and analytics

### Backend

*   RESTful API for all frontend functionalities
*   Secure User Authentication (JWT, Bcrypt)
*   MongoDB database with Mongoose ODM
*   Stripe API integration for:
    *   Customer creation
    *   Payment Intents
    *   Invoice generation
    *   Subscription management
    *   Stripe Connect for vendor payouts
    *   Webhook handling (e.g., for fraud warnings, subscription updates)
*   Activity Logging

## Local Development Setup

To set up and run the entire project locally, follow these steps:

### Prerequisites

*   Node.js (v18 or higher recommended)
*   MongoDB (local instance or cloud service like MongoDB Atlas)
*   Stripe Account (for API keys and webhook setup)

### 1. Backend Setup (`invoice-management-server`)

Navigate to the server directory:

```bash
cd invoice-management-server
```

Install dependencies:

```bash
npm install
```

Create a `.env` file in the `invoice-management-server` directory and add the following environment variables:

```
PORT=5000
MONGO_URI=your_mongodb_connection_string
JWT_SECRET=your_jwt_secret_key
STRIPE_SECRET_KEY=your_stripe_secret_key
STRIPE_WEBHOOK_SECRET=your_stripe_webhook_secret
ADMIN_USERNAME=admin
ADMIN_PASSWORD=adminpass
```

*   Replace placeholders with your actual credentials.
*   `STRIPE_WEBHOOK_SECRET` is for local testing of webhooks. You'll need to use the Stripe CLI for this.

Start the backend server:

```bash
npm start
```

The server will run on `http://localhost:5000`.

### 2. Frontend Setup (`invoice-management-client`)

Open a new terminal and navigate to the client directory:

```bash
cd invoice-management-client
```

Install dependencies:

```bash
npm install
```

Create a `.env.local` file in the `invoice-management-client` directory and add the following environment variables:

```
VITE_API_URL=http://localhost:5000
VITE_STRIPE_PUBLISHABLE_KEY=your_stripe_publishable_key
```

*   Replace `your_stripe_publishable_key` with your actual Stripe publishable key.

Start the frontend development server:

```bash
npm run dev
```

The frontend will typically run on `http://localhost:5173`.

## Deployment

This application is designed for deployment on Vercel. The `vercel.json` file at the root configures the monorepo setup, allowing both the frontend (static build) and backend (serverless functions) to be deployed from a single repository.

For detailed deployment instructions and environment variable configuration on Vercel, refer to the Vercel documentation and the specific `README.md` files for the client and server.

## More Information

*   [Frontend README](invoice-management-client/README.md)
*   [Backend README](invoice-management-server/README.md)
