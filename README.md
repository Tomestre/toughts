# 💭 Toughts - Social Thoughts Sharing Platform

A full-stack web application for sharing thoughts and ideas with the community. Built with Node.js, Express, MySQL, and Sequelize ORM. Features user authentication, thought management, and SQL database with relational models.

## 🚀 Technologies

**Backend:**
- 🟢 Node.js + Express.js
- 🎨 Handlebars (Template Engine)
- 🗄️ MySQL (SQL Database)
- 🔗 Sequelize ORM (v6+)
- 🔐 Bcrypt (Password hashing)
- 📦 Express Session (Session management)
- 💬 Express Flash (Flash messages)

**Database:**
- 🗄️ MySQL Server
- ✨ Sequelize ORM for database abstraction
- 📊 Relational schema with User-Thought relationships

## ✨ Features

✅ **User Authentication**
- Secure signup/login with Bcrypt
- Session-based authentication
- Password security and validation

✅ **Thought Management**
- Create, read, update, delete thoughts
- Browse community thoughts
- Filter thoughts by user
- Timestamp tracking

✅ **Relational Database**
- User model with authentication fields
- Thought model with user associations
- One-to-Many relationships (User → Thoughts)
- Proper SQL schema with foreign keys

✅ **User Interface**
- Handlebars server-side rendering
- Flash messages for user feedback
- Responsive design
- Session persistence

✅ **Full Backend Architecture**
- MVC pattern (Models, Views, Controllers)
- RESTful routing
- Middleware integration
- Error handling

## 📋 Prerequisites

- Node.js (v14 or higher)
- npm or yarn
- MySQL Server running locally

## 💾 Installation

### Clone Repository
bash
git clone https://github.com/Tomestre/toughts.git
cd toughts


### Install Dependencies
bash
npm install


### Database Configuration

Edit `db/conn.js` and update MySQL credentials:

javascript
const sequelize = new Sequelize('toughts2', 'root', 'your_password', {
    host: 'localhost',
    dialect: 'mysql'
})


Create the database:
bash
mysql -u root -p
CREATE DATABASE toughts2;
EXIT;


## ▶️ Running the Application

bash
npm start
# Application runs on http://localhost:3306


Access the application at `http://localhost:3306`

## 📁 Project Structure

```
toughts/
├── db/
│   └── conn.js                 # MySQL connection with Sequelize
├── models/
│   ├── User.js                 # User model with authentication
│   └── Tought.js               # Thought model with relationships
├── controllers/
│   ├── ToughtController.js      # Thought CRUD operations
│   └── AuthController.js        # Authentication logic
├── routes/
│   ├── toughtsRoutes.js         # Thought routes
│   └── authRoutes.js            # Auth routes
├── views/
│   ├── layouts/                 # Handlebars layouts
│   ├── toughts/                 # Thought templates
│   └── auth/                    # Authentication templates
├── public/
│   ├── css/                     # Stylesheets
│   └── js/                      # Client-side scripts
├── index.js                     # Express app setup
└── package.json
```

## 🗄️ Database Schema

### Users Table
```sql
CREATE TABLE Users (
    id INT PRIMARY KEY AUTO_INCREMENT,
    username VARCHAR(100) UNIQUE NOT NULL,
    email VARCHAR(100) UNIQUE NOT NULL,
    password VARCHAR(255) NOT NULL,
    createdAt TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updatedAt TIMESTAMP DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP
);
```

### Thoughts Table
```sql
CREATE TABLE Toughts (
    id INT PRIMARY KEY AUTO_INCREMENT,
    title VARCHAR(255) NOT NULL,
    userId INT NOT NULL,
    createdAt TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updatedAt TIMESTAMP DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP,
    FOREIGN KEY (userId) REFERENCES Users(id) ON DELETE CASCADE
);
```

## 🔌 Routes

### Authentication
- `GET /` - Home page (list all thoughts)
- `GET /register` - Registration form
- `POST /register` - Create new user
- `GET /login` - Login form
- `POST /login` - Authenticate user
- `GET /logout` - Destroy session

### Thoughts
- `GET /toughts` - List all thoughts
- `GET /toughts/add` - Add thought form
- `POST /toughts/add` - Create new thought
- `GET /toughts/edit/:id` - Edit thought form
- `POST /toughts/edit/:id` - Update thought
- `POST /toughts/delete/:id` - Delete thought
- `GET /toughts/user/:id` - List user's thoughts

## 🔒 Security Features

- **Bcrypt Hashing** - Passwords stored securely
- **Sessions** - Server-side session management
- **Flash Messages** - User feedback system
- **CSRF Protection** - Session validation
- **SQL Injection Prevention** - Sequelize parameterized queries

## 🎯 Key Learnings Demonstrated

- ✅ **SQL Database Design** - Relational schema with foreign keys
- ✅ **Sequelize ORM** - Model definitions and relationships
- ✅ **Express Backend** - MVC pattern implementation
- ✅ **Authentication** - Bcrypt hashing and session management
- ✅ **Template Engines** - Handlebars server-side rendering
- ✅ **Database Relationships** - One-to-Many associations
- ✅ **Full CRUD Operations** - Create, Read, Update, Delete
- ✅ **Middleware** - Session, flash messages, routing

## 💡 Use Cases

This project demonstrates:
- Building a complete backend application with SQL
- Working with relational databases and ORM
- User authentication and session management
- MVC architectural pattern
- Server-side rendering with template engines

## 📝 License

ISC

## 👤 Author

Gabriel Tomé (Tomestre)

---

**Perfect for demonstrating:** SQL database expertise, ORM usage (Sequelize), backend development with Express, and relational data modeling