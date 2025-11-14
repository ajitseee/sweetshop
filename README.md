# 🍬 Sweet Shop Management System

A full-stack MERN (MongoDB, Express, React, Node.js) application for managing a sweet shop inventory with user authentication, role-based access control, and comprehensive testing.

## 📋 Table of Contents

- [Features](#features)
- [Tech Stack](#tech-stack)
- [Project Structure](#project-structure)
- [Setup Instructions](#setup-instructions)
- [API Endpoints](#api-endpoints)
- [Testing](#testing)
- [My AI Usage](#my-ai-usage)
- [Screenshots](#screenshots)
- [Deployment](#deployment)

## ✨ Features

### User Features
- 🔐 User registration and authentication with JWT
- 🔍 Search and filter sweets by name, category, and price range
- 🛒 Purchase sweets (decreases inventory)
- 📊 View real-time inventory status

### Admin Features
- ➕ Add new sweets to inventory
- ✏️ Update sweet details
- 🗑️ Delete sweets from inventory
- 📦 Restock sweets (increase quantity)

### Technical Features
- 🧪 Test-Driven Development (TDD) approach
- 🔒 Protected routes with role-based access control
- ✅ Input validation on both frontend and backend
- 📱 Responsive design for mobile and desktop
- 🎨 Modern, beautiful UI with gradient designs

## 🛠️ Tech Stack

### Backend
- **Runtime**: Node.js
- **Framework**: Express.js
- **Language**: TypeScript
- **Database**: MongoDB with Mongoose ODM
- **Authentication**: JWT (JSON Web Tokens)
- **Password Hashing**: bcryptjs
- **Testing**: Jest & Supertest
- **Validation**: express-validator

### Frontend
- **Library**: React
- **Routing**: React Router v6
- **HTTP Client**: Axios
- **Styling**: CSS3 with modern gradients and animations

## 📁 Project Structure

```
sweetshopproject/
├── backend/
│   ├── src/
│   │   ├── config/
│   │   │   └── database.ts          # MongoDB connection
│   │   ├── controllers/
│   │   │   ├── authController.ts    # Authentication logic
│   │   │   └── sweetController.ts   # Sweet CRUD operations
│   │   ├── middleware/
│   │   │   └── auth.ts              # JWT & admin middleware
│   │   ├── models/
│   │   │   ├── User.ts              # User schema
│   │   │   └── Sweet.ts             # Sweet schema
│   │   ├── routes/
│   │   │   ├── authRoutes.ts        # Auth endpoints
│   │   │   └── sweetRoutes.ts       # Sweet endpoints
│   │   ├── services/
│   │   │   ├── authService.ts       # Auth business logic
│   │   │   ├── authService.test.ts  # Auth tests
│   │   │   ├── sweetService.ts      # Sweet business logic
│   │   │   └── sweetService.test.ts # Sweet tests
│   │   ├── app.ts                   # Express app setup
│   │   └── server.ts                # Server entry point
│   ├── .env
│   ├── package.json
│   ├── tsconfig.json
│   └── jest.config.js
│
└── src/                             # React frontend
    ├── components/
    │   ├── Login.js                 # Login form
    │   ├── Register.js              # Registration form
    │   ├── Dashboard.js             # Main dashboard
    │   ├── SweetCard.js             # Sweet display card
    │   ├── AddSweetModal.js         # Add sweet modal
    │   ├── ProtectedRoute.js        # Route protection
    │   └── *.css                    # Component styles
    ├── context/
    │   └── AuthContext.js           # Authentication context
    ├── services/
    │   └── api.js                   # API client
    ├── App.js                       # Main app component
    └── index.js                     # App entry point
```

## 🚀 Setup Instructions

### Prerequisites
- Node.js (v14 or higher)
- MongoDB Atlas account (already configured)
- npm or yarn package manager

### Backend Setup

1. **Navigate to backend directory:**
   ```bash
   cd backend
   ```

2. **Install dependencies:**
   ```bash
   npm install
   ```

3. **Environment variables are already configured in `.env`:**
   ```
   PORT=5000
   MONGODB_URI=mongodb+srv://ajits205070:as5759423@cluster0.rfk3tfn.mongodb.net/sweetshop
   JWT_SECRET=sweetshop_secret_key_change_in_production_2025
   NODE_ENV=development
   ```

4. **Run tests:**
   ```bash
   npm test
   ```

5. **Start the backend server:**
   ```bash
   npm run dev
   ```

   The backend will run on `http://localhost:5000`

### Frontend Setup

1. **Navigate to project root:**
   ```bash
   cd ..
   ```

2. **Dependencies are already installed. Start the React development server:**
   ```bash
   npm start
   ```

   The frontend will run on `http://localhost:3000`

### Creating an Admin User

To test admin features:

1. Register a normal user through the UI at `http://localhost:3000/register`
2. Manually update the user's role in MongoDB Atlas:
   - Go to MongoDB Atlas Dashboard
   - Browse Collections → sweetshop → users
   - Find your user and edit the `role` field from `"user"` to `"admin"`
3. Log out and log back in to see admin features

## 📡 API Endpoints

### Authentication Routes

| Method | Endpoint | Description | Access |
|--------|----------|-------------|--------|
| POST | `/api/auth/register` | Register new user | Public |
| POST | `/api/auth/login` | Login user | Public |

### Sweet Routes

| Method | Endpoint | Description | Access |
|--------|----------|-------------|--------|
| GET | `/api/sweets` | Get all sweets | Authenticated |
| GET | `/api/sweets/search` | Search sweets | Authenticated |
| POST | `/api/sweets` | Create new sweet | Admin only |
| PUT | `/api/sweets/:id` | Update sweet | Admin only |
| DELETE | `/api/sweets/:id` | Delete sweet | Admin only |
| POST | `/api/sweets/:id/purchase` | Purchase sweet | Authenticated |
| POST | `/api/sweets/:id/restock` | Restock sweet | Admin only |

## 🧪 Testing

The project follows Test-Driven Development (TDD) principles. Tests are written using Jest and Supertest.

### Running Tests

```bash
cd backend
npm test
```

### Test Coverage

```bash
npm test -- --coverage
```

### Test Structure

- **Unit Tests**: Service layer testing with mocked dependencies
- **Integration Tests**: API endpoint testing (can be added)
- **Test Files**: 
  - `authService.test.ts` - Authentication service tests
  - `sweetService.test.ts` - Sweet service tests

### Example Test Cases

✅ User registration with valid data  
✅ User login with correct credentials  
✅ Duplicate user registration prevention  
✅ Invalid credentials handling  
✅ Sweet creation and retrieval  
✅ Search functionality  
✅ Purchase with stock validation  
✅ Restock functionality  

## 🤖 My AI Usage

### AI Tools Used

I used **GitHub Copilot** extensively throughout this project to accelerate development while maintaining code quality and following best practices.

### How I Used AI

#### 1. **Project Structure & Setup**
- Used Copilot to generate initial project structure and boilerplate code
- Generated package.json configurations for both frontend and backend
- Created TypeScript configuration files with appropriate compiler options

#### 2. **Backend Development**
- **Models**: Copilot suggested Mongoose schema structures with proper validation rules
- **Services**: Generated initial service class structures following the service pattern
- **Controllers**: Created controller boilerplate with proper error handling
- **Middleware**: Generated JWT authentication and admin authorization middleware
- **Routing**: Suggested RESTful route structures with appropriate HTTP methods

#### 3. **Test-Driven Development**
- Copilot helped generate comprehensive test suites for services
- Suggested edge cases and error scenarios to test
- Generated mock implementations for database operations
- Helped structure test cases following the AAA (Arrange-Act-Assert) pattern

#### 4. **Frontend Development**
- Generated React component structures with hooks
- Created context providers for authentication
- Suggested responsive CSS designs with modern gradients
- Implemented form validation logic
- Created reusable components with proper prop handling

#### 5. **API Integration**
- Generated Axios configurations with interceptors
- Created API service layer for clean separation of concerns
- Implemented error handling for network requests

#### 6. **Styling**
- Copilot suggested modern CSS with gradients and animations
- Generated responsive design patterns
- Created consistent styling across components

### My Workflow with AI

1. **Red Phase (TDD)**: Wrote test descriptions, Copilot suggested test implementations
2. **Green Phase**: Implemented features with Copilot suggestions, manually refined logic
3. **Refactor Phase**: Used Copilot to improve code structure and remove duplication

### Reflection on AI Impact

**Positive Impacts:**
- ⚡ **Speed**: Reduced development time by approximately 40-50%
- 📚 **Learning**: Discovered new patterns and best practices through suggestions
- 🎯 **Focus**: Allowed me to focus on business logic rather than boilerplate
- ✅ **Testing**: Helped ensure comprehensive test coverage

**Challenges & Manual Work:**
- 🔍 **Review Required**: Always reviewed AI-generated code for correctness
- 🎨 **Custom Logic**: Business-specific logic required manual implementation
- 🔧 **Integration**: Some integration points needed manual adjustment
- 📝 **Documentation**: This README structure and content was AI-assisted but manually refined

**Key Takeaway:**  
AI tools like Copilot are excellent accelerators but not replacements for understanding. I treated Copilot as a pair programmer - suggesting solutions that I then evaluated, modified, and integrated thoughtfully into the codebase.

### Transparency Commitment

Throughout development, I:
- ✅ Reviewed all AI-generated code before committing
- ✅ Modified suggestions to fit project requirements
- ✅ Tested all functionality thoroughly
- ✅ Understood every line of code in the project
- ✅ Am prepared to discuss and modify any part during interviews

## 📸 Screenshots

_Screenshots will be added after running the application_

### Login Page
*User-friendly login interface with gradient design*

### Registration Page
*Registration form with validation*

### Dashboard
*Main dashboard showing all available sweets with search and filters*

### Sweet Card
*Individual sweet card with purchase option*

### Admin Features
*Admin view with add, edit, delete, and restock options*

## 🚀 Deployment

### Backend Deployment (Heroku Example)

```bash
# Install Heroku CLI and login
heroku login

# Create new app
heroku create sweetshop-api

# Set environment variables
heroku config:set MONGODB_URI=mongodb+srv://ajits205070:as5759423@cluster0.rfk3tfn.mongodb.net/sweetshop
heroku config:set JWT_SECRET=sweetshop_secret_key_change_in_production_2025
heroku config:set NODE_ENV=production

# Deploy
git subtree push --prefix backend heroku main
```

### Frontend Deployment (Vercel Example)

```bash
# Install Vercel CLI
npm i -g vercel

# Deploy
vercel

# Set environment variables in Vercel dashboard
REACT_APP_API_URL=https://your-backend-url.herokuapp.com/api
```

## 👥 Contributing

This is a student project for campus placements. However, feedback and suggestions are welcome!

## 📝 License

This project is created for educational purposes.

## 🙏 Acknowledgments

- Thanks to the placement team for this challenging and educational assignment
- Thanks to GitHub Copilot for accelerating development
- Thanks to the open-source community for amazing tools

---

## 🎯 Quick Start Guide

1. **Start Backend:**
   ```bash
   cd backend
   npm run dev
   ```

2. **Start Frontend (in new terminal):**
   ```bash
   npm start
   ```

3. **Create account** at http://localhost:3000/register

4. **Make yourself admin** via MongoDB Atlas to test admin features

5. **Start managing sweets!** 🍬

---

**Database**: MongoDB Atlas is already connected and ready to use!

### Analyzing the Bundle Size

This section has moved here: [https://facebook.github.io/create-react-app/docs/analyzing-the-bundle-size](https://facebook.github.io/create-react-app/docs/analyzing-the-bundle-size)

### Making a Progressive Web App

This section has moved here: [https://facebook.github.io/create-react-app/docs/making-a-progressive-web-app](https://facebook.github.io/create-react-app/docs/making-a-progressive-web-app)

### Advanced Configuration

This section has moved here: [https://facebook.github.io/create-react-app/docs/advanced-configuration](https://facebook.github.io/create-react-app/docs/advanced-configuration)

### Deployment

This section has moved here: [https://facebook.github.io/create-react-app/docs/deployment](https://facebook.github.io/create-react-app/docs/deployment)

### `npm run build` fails to minify

This section has moved here: [https://facebook.github.io/create-react-app/docs/troubleshooting#npm-run-build-fails-to-minify](https://facebook.github.io/create-react-app/docs/troubleshooting#npm-run-build-fails-to-minify)
