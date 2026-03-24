# ShopConsole

ShopConsole is a full-stack product management web application built with the MERN ecosystem.  
It provides a clean UI for creating, viewing, updating, and deleting products, backed by a REST API and MongoDB persistence.

Live demo: [https://shopconsole.onrender.com/](https://shopconsole.onrender.com/)

## Table of Contents

- [Overview](#overview)
- [Tech Stack](#tech-stack)
- [Features](#features)
- [Project Structure](#project-structure)
- [Getting Started](#getting-started)
- [Environment Variables](#environment-variables)
- [Available Scripts](#available-scripts)
- [API Reference](#api-reference)
- [Build and Deployment](#build-and-deployment)
- [Troubleshooting](#troubleshooting)
- [License](#license)

## Overview

ShopConsole is designed as a simple but production-style CRUD system:

- `backend`: Express API with Mongoose models and controllers
- `frontend`: React + Vite single-page application
- Unified deployment option where the backend serves the built frontend in production

## Tech Stack

### Backend

- Node.js
- Express
- MongoDB + Mongoose
- dotenv

### Frontend

- React
- Vite
- React Router
- Chakra UI
- Zustand

## Features

- Create products with name, price, and image URL
- View all products in a responsive card grid
- Update product details via modal form
- Delete products with immediate UI updates
- Toast notifications for success/error states
- Light/dark mode toggle
- Production-ready static frontend serving through Express

## Project Structure

```text
ShopConsole/
├── backend/
│   ├── config/
│   │   └── db.js
│   ├── controllers/
│   │   └── product.controller.js
│   ├── models/
│   │   └── product.model.js
│   ├── routes/
│   │   └── product.route.js
│   └── server.js
├── frontend/
│   ├── src/
│   │   ├── components/
│   │   ├── pages/
│   │   ├── store/
│   │   ├── App.jsx
│   │   └── main.jsx
│   └── package.json
└── package.json
```

## Getting Started

### Prerequisites

- Node.js 18+ recommended
- npm 9+ recommended
- A MongoDB instance (local or cloud)

### 1) Clone and install dependencies

```bash
git clone <your-repo-url>
cd ShopConsole
npm install
npm install --prefix frontend
```

### 2) Configure environment variables

Create a `.env` file in the project root:

```env
MONGO_URI=your_mongodb_connection_string
PORT=5001
NODE_ENV=development
```

### 3) Run in development

```bash
npm run dev
```

Then open [http://localhost:5001](http://localhost:5001).

## Environment Variables

| Variable | Required | Description |
| --- | --- | --- |
| `MONGO_URI` | Yes | MongoDB connection string used by Mongoose |
| `PORT` | No | Server port (defaults to `5001`) |
| `NODE_ENV` | No | Runtime environment (`development` or `production`) |

## Available Scripts

From the project root:

- `npm run dev` - starts backend with `nodemon` in development mode
- `npm run build` - installs dependencies and builds the frontend bundle
- `npm start` - starts the backend in production mode

From `frontend/`:

- `npm run dev` - starts Vite development server
- `npm run build` - creates production frontend assets
- `npm run preview` - previews the production build locally
- `npm run lint` - runs ESLint checks

## API Reference

Base path: `/api/products`

### `GET /api/products`

Fetch all products.

Response:

```json
{
  "success": true,
  "data": [
    {
      "_id": "67f0f5a2d7...",
      "name": "Keyboard",
      "price": 79.99,
      "image": "https://example.com/image.png",
      "createdAt": "2026-03-24T12:00:00.000Z",
      "updatedAt": "2026-03-24T12:00:00.000Z"
    }
  ]
}
```

### `POST /api/products`

Create a new product.

Request body:

```json
{
  "name": "Keyboard",
  "price": 79.99,
  "image": "https://example.com/image.png"
}
```

### `PUT /api/products/:id`

Update a product by MongoDB ObjectId.

### `DELETE /api/products/:id`

Delete a product by MongoDB ObjectId.

## Build and Deployment

For production deployment:

1. Build frontend assets:

   ```bash
   npm run build
   ```

2. Start the server:

   ```bash
   npm start
   ```

In production mode, Express serves the compiled frontend from `frontend/dist` and handles SPA route fallbacks.

## Troubleshooting

- Ensure `MONGO_URI` is valid and reachable from your runtime environment.
- If frontend updates are not reflected in production, run `npm run build` again.
- If port conflicts occur, set a custom `PORT` in `.env`.

## License

This project is licensed under the ISC License.
