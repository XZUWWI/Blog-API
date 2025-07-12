# 📝 Blog API

A fully functional, production-ready **RESTful Blog API** built with **Node.js**, **Express.js**, and **MongoDB**.

---

## 🚀 Features

### 🔒 Core Functionality

* **User Authentication** — Secure JWT-based login & registration
* **Post Management** — Full CRUD for blog posts
* **Comments System** — Nested commenting with replies
* **Role-Based Access** — Admin and regular user roles
* **Validation** — Strong input validation using express-validator
* **Central Error Handling** — Unified, consistent responses

### ✨ Additional Features

* **Pagination & Search** — For efficient post retrieval
* **Sort Options** — newest, oldest, views, comments, featured
* **Admin Powers** — Admins can delete any post or comment
* **View Tracking** — Records post view count
* **Post Status** — Draft or published
* **Featured Posts** — Highlight key content
* **Tags System** — Organize posts by topics

---

## 📁 Project Structure

```
blog-api/
├── config/               # Database setup
├── controllers/          # Route logic
├── middleware/           # Auth, validation, error handlers
├── models/               # Mongoose schemas
├── routes/               # API endpoints
├── server.js             # App entry point
├── package.json
└── .env / README.md
```

---

## ⚙️ Setup Instructions

### 1. Clone Repository

```bash
git clone https://github.com/XZUWWI/Blog-API.git
cd blog-api
```

### 2. Install Dependencies

```bash
npm install
```

### 3. Configure Environment Variables

Create a `.env` file in the root:

```env
PORT=3000
MONGODB_URI=mongodb://localhost:27017/blog-api
JWT_SECRET=your-super-secret-jwt-key
NODE_ENV=development
```

### 4. Start MongoDB

Ensure MongoDB is running locally or use MongoDB Atlas.

### 5. Run the App

```bash
# Development
npm run dev

# Production
npm start
```

---

## 🌐 API Overview

### Base URL

```
http://localhost:3000/api
```

---

## 🔐 Authentication Endpoints

### ➕ Register

```http
POST /api/users/register
```

```json
{
  "username": "zrxxz",
  "email": "zrxxz@example.com",
  "password": "password123"
}
```

### 🔑 Login

```http
POST /api/users/login
```

```json
{
  "email": "zrxxz@example.com",
  "password": "password123"
}
```

### 👤 Get User Profile

```http
GET /api/users/profile
Authorization: Bearer <token>
```

---

## 📝 Posts API

### 📄 Get All Posts

```http
GET /api/posts?page=1&limit=10&search=js&sort=newest&status=published
```

### 📥 Create Post

```http
POST /api/posts
Authorization: Bearer <token>
```

```json
{
  "title": "New Post",
  "content": "Content here...",
  "tags": ["javascript", "nodejs"],
  "status": "published",
  "featured": false
}
```

### 🔄 Update Post

```http
PUT /api/posts/:id
Authorization: Bearer <token>
```

### ❌ Delete Post

```http
DELETE /api/posts/:id
Authorization: Bearer <token>
```

### 🔍 Get Single Post

```http
GET /api/posts/:id
```

### 📚 Get My Posts

```http
GET /api/posts/my-posts?page=1&limit=10&status=published
Authorization: Bearer <token>
```

---

## 💬 Comments API

### 💬 Get Comments for a Post

```http
GET /api/comments/posts/:id/comments?page=1&limit=20
```

### ➕ Add Comment

```http
POST /api/comments/posts/:id/comments
Authorization: Bearer <token>
```

```json
{
  "content": "Great post!",
  "parentComment": "comment_id" // Optional
}
```

### ✏️ Update Comment

```http
PUT /api/comments/:id
Authorization: Bearer <token>
```

### 🗑 Delete Comment

```http
DELETE /api/comments/:id
Authorization: Bearer <token>
```

### 🔎 Get Single Comment

```http
GET /api/comments/:id
```

---

## 🔐 Authentication

Use JWT tokens in headers:

```
Authorization: Bearer <your-token>
```

---

## 📊 Unified API Responses

### ✅ Success

```json
{
  "success": true,
  "message": "Success",
  "data": { ... }
}
```

### ❌ Error

```json
{
  "success": false,
  "message": "Validation failed",
  "errors": [
    { "field": "email", "message": "Invalid email", "value": "bad" }
  ]
}
```

---

## 🧪 Test with Postman

1. Import endpoints manually or with a Postman collection
2. Create environment variables:

   * `base_url`: `http://localhost:3000/api`
   * `token`: (auto-filled after login)
3. Test flow:

   * Register → Login → Set token → Use endpoints

---

## 🚀 Deployment Tips

### Production Environment Example

```env
PORT=3000
MONGODB_URI=your-mongodb-uri
JWT_SECRET=your-secure-jwt-secret
NODE_ENV=production
```

### With PM2

```bash
npm install -g pm2
pm2 start server.js --name "blog-api"
pm2 save
pm2 startup
```

---

## 🔧 Developer Notes

* Follow RESTful principles
* Validate all input data
* Use `express-validator`
* Always return consistent response shapes

---

## 📝 License

MIT License — Open for public use with attribution.

---

## 🤝 Contributions

Contributions are welcome!

1. Fork the repo
2. Create a branch
3. Make your changes
4. Submit a PR

---

## 📞 Support

For help, open an issue or reach out via Discord (if applicable).
