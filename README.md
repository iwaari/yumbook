# YumBook - The Ultimate Recipe API 🍽️

## 📌 About YumBook
**YumBook** is a **modern recipe management API** designed with **Node.js, Express.js, and MongoDB**.  
This API enables users to **store, update, organize, and share** their favorite recipes.  
With built-in authentication, user profile management, and recipe categorization, YumBook makes it easier than ever to explore the world of cooking.

---

## ✨ Key Features
- 🔑 **Secure User Authentication** (JWT-based)
- 📝 **Recipe CRUD Operations** (Create, Read, Update, Delete)
- 📂 **User Profile Management**
- 🌍 **Cloud Database Integration (MongoDB Atlas)**
- 🔒 **Authentication Middleware for Protected Routes**

---

## 🚀 Getting Started
### 🏗️ **1. Clone the Repository**
```sh
git clone https://github.com/YOUR_GITHUB_USERNAME/YumBook.git
cd YumBook/backend
```

### 📦 **2. Install Required Packages**
```sh
npm install
```

### 🔧 **3. Configure Environment Variables**
Create a `.env` file in the project's root folder and add the following:

```plaintext
MONGO_URI= your_mongodb_string
DB_NAME= your_database_name
JWT_SECRET= your_token
PORT=5000

```

### ▶️ **4. Start the API Server**
```sh
npm start
```
The backend service will be live at `http://localhost:5000/`.

---

## 📚 API Documentation
### 🔐 **Authentication Endpoints**
#### ✅ **1. Register a New User**
```http
POST /register
```
📥 **Request Body:**
```json
{
    "username": "chefMaster",
    "email": "chef@example.com",
    "password": "securePass123"
}
```
📤 **Response:**
```json
{
    "message": "Welcome aboard! Your account has been created."
}
```

#### 🔓 **2. User Login**
```http
POST /login
```
📥 **Request Body:**
```json
{
    "email": "chef@example.com",
    "password": "securePass123"
}
```
📤 **Response:**
```json
{
    "token": "your_generated_jwt_token",
    "user": {
        "id": "unique_user_id",
        "username": "chefMaster",
        "email": "chef@example.com"
    }
}
```

---

### 🏠 **User Management**
#### 🔎 **3. Fetch User Profile**
```http
GET /users/profile
Authorization: Bearer <your_jwt_token>
```
📤 **Response:**
```json
{
    "_id": "user_unique_id",
    "username": "chefMaster",
    "email": "chef@example.com"
}
```

#### ✏️ **4. Edit User Profile**
```http
PUT /users/profile
Authorization: Bearer <your_jwt_token>
```
📥 **Request Body:**
```json
{
    "username": "newChefName",
    "email": "new_email@example.com"
}
```
📤 **Response:**
```json
{
    "message": "Profile updated successfully!"
}
```

---

### 🍽️ **Recipe Management**
#### 📌 **5. Add a New Recipe**
```http
POST /recipes
Authorization: Bearer <your_jwt_token>
```
📥 **Request Body:**
```json
{
    "title": "Spaghetti Bolognese",
    "ingredients": ["Spaghetti", "Ground Beef", "Tomato Sauce", "Garlic", "Onion"],
    "instructions": "Cook pasta, prepare the sauce, mix together, and enjoy!"
}
```
📤 **Response:**
```json
{
    "_id": "recipe_unique_id",
    "title": "Spaghetti Bolognese",
    "ingredients": ["Spaghetti", "Ground Beef", "Tomato Sauce", "Garlic", "Onion"],
    "instructions": "Cook pasta, prepare the sauce, mix together, and enjoy!",
    "user": "user_id"
}
```

#### 📖 **6. Retrieve All Recipes**
```http
GET /recipes
Authorization: Bearer <your_jwt_token>
```
📤 **Response:**
```json
[
    {
        "_id": "recipe1",
        "title": "Spaghetti Bolognese",
        "ingredients": ["Spaghetti", "Ground Beef", "Tomato Sauce", "Garlic", "Onion"],
        "user": {
            "_id": "user1",
            "username": "chefMaster"
        }
    },
    {
        "_id": "recipe2",
        "title": "Tiramisu",
        "ingredients": ["Coffee", "Mascarpone", "Eggs", "Sugar", "Cocoa Powder"],
        "user": {
            "_id": "user2",
            "username": "dessertQueen"
        }
    }
]
```

#### 🔍 **7. Fetch a Specific Recipe**
```http
GET /recipes/:id
Authorization: Bearer <your_jwt_token>
```

#### ✏️ **8. Modify an Existing Recipe**
```http
PUT /recipes/:id
Authorization: Bearer <your_jwt_token>
```
📥 **Request Body:**
```json
{
    "title": "Spaghetti Arrabiata",
    "ingredients": ["Spaghetti", "Tomato Sauce", "Chili Peppers"],
    "instructions": "Boil pasta, prepare spicy sauce, mix and serve!"
}
```
📤 **Response:**
```json
{
    "message": "Recipe has been updated successfully!"
}
```

#### 🗑️ **9. Remove a Recipe**
```http
DELETE /recipes/:id
Authorization: Bearer <your_jwt_token>
```
📤 **Response:**
```json
{
    "message": "The recipe has been successfully removed!"
}
```

---

## 🌍 Deployment Guide
You can deploy **YumBook API** on **Railway, Render, or Fly.io**.

### **Deploy to Railway**
1. **Push Code to GitHub**
```sh
git add .
git commit -m "Deploy API"
git push origin main
```
2. **Deploy on Railway**
   - Visit [Railway](https://railway.app/)
   - Link your GitHub repository
   - Set environment variables (`MONGO_URI`, `JWT_SECRET`, `SESSION_SECRET`)
   - Click **Deploy** 🎉

3. **Test API Endpoint**
```sh
curl -X GET https://your-deployed-url.com/recipes
```

---

## 📝 License
This project is **open-source** and distributed under the **MIT License**.  
Feel free to **contribute, modify, and improve** the project! 🚀
