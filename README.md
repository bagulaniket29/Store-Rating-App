# 🏪 Store Rating Web App

A full-stack web application that allows users to rate stores, store owners to manage their store ratings, and administrators to manage users and stores. Built using React, Express.js, and MySQL.

---

## 🚀 Features

### 👤 Role-Based Access:
- **Admin**:
  - Add/view/update/delete users and store owners
  - Add/view/update/delete stores
  - Dashboard with stats and analytics

- **Store Owner**:
  - View ratings for their own store(s)
  - Update store details

- **Normal User**:
  - View list of stores
  - Submit ratings and reviews

---

## 🛠 Tech Stack

| Layer       | Technology                               |
|-------------|------------------------------------------|
| Frontend    | React.js, Tailwind CSS                      |
| Backend     | Express.js (Node.js)                     |
| Database    | MySQL                                    |
| Tools       | Axios, React Router, dotenv, bcrypt, JWT |

---

## 📁 Project Structure

├── frontend/ # React frontend
│ ├── node_modules/
│ ├── public/
│ ├── src/
│ │ ├── components/ # Reusable UI components
│ │ ├── data/ # used data
│ │ ├── pages/ # Role-based pages (Admin, User, Owner)
│ │ ├── App.jsx
│ │ └── main.jsx
│ │ └── Module.jsx
├── backend/ # Express backend
│ ├── routes/
│ ├── controllers/
│ ├── node_modules/
│ ├── config/
│ ├── server.js
│ ├── .env # Database define
├── .env
├── README.md # All required instruction present here(Prefer this file to run the code)
└── package.json




---

## ⚙️ Setup Instructions

################## DATABASE Design ############################################################

CREATE DATABASE IF NOT EXISTS store_rating;
USE store_rating;

-- Users Table
CREATE TABLE users (
  id INT AUTO_INCREMENT PRIMARY KEY,
  name VARCHAR(100) NOT NULL,
  email VARCHAR(100) NOT NULL UNIQUE,
  password VARCHAR(255) NOT NULL,
  address TEXT,
  role ENUM('admin', 'owner', 'user') NOT NULL,
  created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

-- Stores Table
CREATE TABLE stores (
  id INT AUTO_INCREMENT PRIMARY KEY,
  name VARCHAR(100) NOT NULL,
  address TEXT,
  owner_id INT NOT NULL,
  created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
  FOREIGN KEY (owner_id) REFERENCES users(id) ON DELETE CASCADE
);

-- Ratings Table
CREATE TABLE ratings (
  id INT AUTO_INCREMENT PRIMARY KEY,
  user_id INT NOT NULL,
  store_id INT NOT NULL,
  rating INT CHECK (rating BETWEEN 1 AND 5),
  review TEXT,
  created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
  FOREIGN KEY (user_id) REFERENCES users(id) ON DELETE CASCADE,
  FOREIGN KEY (store_id) REFERENCES stores(id) ON DELETE CASCADE
);





################## 🔧 Backend Setup ############################################################

1. **Clone the repo:**
   ```bash
   git clone https://github.com/yourusername/store-rating-app.git
   cd store-rating-app/backend


2. Install dependencies:

    npm install


3. Configure .env:
    **Create a .env file in backend/:

    PORT=5000
    DB_HOST=localhost
    DB_USER=yourusername
    DB_PASSWORD=yourpassword
    DB_NAME=store_rating


4. Start the backend server:

    npm run dev



################## 🌐 Frontend Setup ############################################################

1. Open a new terminal and go to the frontend folder:

    cd ../frontend


2. Install dependencies:

    npm install


3. Run the React app:
 
    npm run dev / npm start

***The frontend will run on http://localhost:3000 and backend on http://localhost:5000






✅ Login Roles(Exxample)
Email	            | Password	| Role      |
--------------------------------------------|
admin@example.com	| Admin@123	| Admin     |
owner@example.com	| Owner@123	| Owner     |
user@example.com	| User@123	| User      |




🙌 Author
Aniket Bharat Bagul
LinkedIn : https://www.linkedin.com/in/aniketbagul29/  
GitHub : https://github.com/BAGULANIKET29
Portfolio : https://aniketbagul.netlify.app/

