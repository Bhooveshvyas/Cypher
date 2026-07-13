# 🔐 Cypher

> A Zero-Knowledge encrypted text sharing platform where your secrets never leave your browser.

![Next.js](https://img.shields.io/badge/Next.js-000?logo=next.js)
![Node.js](https://img.shields.io/badge/Node.js-339933?logo=node.js)
![Express](https://img.shields.io/badge/Express-black?logo=express)
![MongoDB](https://img.shields.io/badge/MongoDB-47A248?logo=mongodb)
![License](https://img.shields.io/badge/license-MIT-blue)

## Live Demo

🔗 **https://cypher-nu.vercel.app/**

---

## Overview

Cypher is a secure secret-sharing application inspired by services like PrivateBin and One-Time Secret.

Unlike conventional applications where servers can potentially access user data, Cypher follows a **Zero-Knowledge Architecture**.

- Secrets are encrypted **inside the browser**
- The server **never receives plaintext**
- MongoDB stores **only encrypted ciphertext**
- Decryption keys are **never transmitted to the backend**

Even if the database is leaked, attackers cannot recover the original secret.

---

# Features

- 🔐 Client-side AES-256 encryption
- 🛡️ Zero-Knowledge Architecture
- ⏳ Configurable expiry time
- 👀 Configurable read limits
- 🗑 Automatic deletion after expiration or read limit
- ⚡ Fast Next.js frontend
- 🌐 REST API with Express.js
- ☁️ MongoDB persistence
- 🚀 Deployed on Vercel

---

# How It Works

```text
                User Types Secret
                        │
                        ▼
        AES-256 Encryption (Browser)
                        │
                        ▼
          Encrypted Ciphertext Only
                        │
                        ▼
              Express.js Backend
                        │
                        ▼
                  MongoDB Storage
                        │
                        ▼
          Recipient Opens Shared Link
                        │
                        ▼
    Browser Retrieves Ciphertext + URL Key
                        │
                        ▼
          Local Browser Decryption
```

## Why is it Zero-Knowledge?

The encryption key is placed inside the **URL Fragment**.

```
https://cypher.vercel.app/decode-secret?id=abc123#Qh82Kd9sL...
```

Notice everything after `#`.

Browsers **never send the URL fragment to the server**.

That means the backend receives only

```
/decode-secret?id=abc123
```

and **never**

```
#Qh82Kd9sL...
```

As a result,

- Backend cannot decrypt secrets.
- MongoDB stores only ciphertext.
- Server administrators cannot read user data.
- Even a database breach exposes only encrypted blobs.

---

# Tech Stack

## Frontend

- Next.js
- React
- JavaScript

## Backend

- Node.js
- Express.js

## Database

- MongoDB

## Deployment

- Vercel

---

# Project Structure

```text
Cypher
│
├── backend
│   ├── client
│   │   └── mongoClient.js
│   ├── constants
│   │   └── config.js
│   ├── routes
│   │   └── storeRoutes.js
│   ├── utils
│   │   └── validator.js
│   ├── app.js
│   ├── server.js
│   └── vercel.json
│
├── frontend
│   ├── components
│   ├── pages
│   │   ├── share-secret
│   │   ├── decode-secret
│   │   └── secure-files
│   ├── public
│   └── utils
│       └── encryption.js
│
└── README.md
```

---

# Running Locally

## Clone the repository

```bash
git clone https://github.com/Bhooveshvyas/Cypher.git
cd Cypher
```

## Backend

```bash
cd backend
npm install
npm run dev
```

## Frontend

```bash
cd frontend
npm install
npm run dev
```

---

# Security Highlights

✅ Plaintext never leaves the browser

✅ AES-256 encryption performed client-side

✅ Only encrypted ciphertext stored in MongoDB

✅ Encryption key never reaches the backend

✅ Read-once secrets supported

✅ Auto-expiring secrets

✅ Zero-Knowledge implementation

---

# Future Improvements

- Password-protected secrets
- File encryption support
- QR-code sharing
- Custom deletion policies
- Secret history
- Anonymous analytics
- End-to-End encrypted file sharing

---

# Author

**Bhoovesh Vyas**

GitHub: https://github.com/Bhooveshvyas

LinkedIn: https://linkedin.com/in/bhooveshvyas
