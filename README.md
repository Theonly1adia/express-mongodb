# MongoDB and Express Assignment

## Objective
Learn MongoDB basics, set up a MongoDB Atlas account, connect to it using Mongoose in an Express app, and deploy your app.

---

## Steps Overview

### 1. Introduction to MongoDB
- MongoDB is a NoSQL database storing data in JSON-like documents.
- Key features: document-oriented, schema-less, and scalable.

### 2. Setting Up MongoDB Atlas
1. Create a free account on [MongoDB Atlas](https://www.mongodb.com/cloud/atlas).
2. Create a cluster and database user.
3. Whitelist your IP address.
4. Obtain your connection string from "Clusters > Connect > Connect Your Application."

### 3. Connecting MongoDB to an Express App
1. Initialize the project:
   ```bash
   mkdir express-mongodb
   cd express-mongodb
   npm init -y
   npm install express mongoose dotenv
   ```
2. Create `index.js`:
   ```javascript
   const express = require('express');
   const mongoose = require('mongoose');
   const app = express();
   const port = 3000;

   require('dotenv').config(); // Load .env file

   app.use(express.json()); // Middleware

   mongoose.connect(process.env.MONGO_URI, {
     useNewUrlParser: true,
     useUnifiedTopology: true,
   })
   .then(() => console.log('Connected to MongoDB'))
   .catch(err => console.error('Error connecting:', err));

   app.get('/', (req, res) => res.send('Hello, World!'));

   app.listen(port, () => console.log(`Server running on http://localhost:${port}`));
   ```
3. Store your connection string in a `.env` file:
   ```env
   MONGO_URI=your-mongodb-connection-string
   ```
4. Add `.env` to `.gitignore` to keep it private.
5. Test the app locally and ensure "Connected to MongoDB" appears in the console.

### 4. Deploying the App
1. Sign up at [Render](https://render.com/).
2. Push your project to GitHub.
3. Add `MONGO_URI` as an environment variable on Render.
4. Deploy your app and verify it works at the provided URL.

---

## Summary
This assignment covers MongoDB setup, connecting it to an Express app, and deploying the app. By the end, you’ll have a functional, deployed application with a MongoDB backend.

