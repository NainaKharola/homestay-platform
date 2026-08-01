# 🏡 HomeStay

HomeStay is a **full-stack MERN web application** developed as part of the **AI-Assisted Full Stack Web Development Internship**.

The platform allows users to discover, create, manage, and update homestay property listings through a modern React interface while an Express.js backend provides secure REST APIs. Property data is stored in **MongoDB Atlas**, authentication is handled using **JWT** and **Google OAuth**, and an **AI-powered Property Description Generator** helps hosts create professional listing descriptions using **Google Gemini**.

---

# ✨ Features

## 👤 Authentication
- Email & Password Registration/Login
- Google OAuth 2.0 Login
- JWT Authentication
- Protected Routes
- Persistent User Session

## 🏠 Property Management
- Create Property
- View All Properties
- View Property Details
- Edit Property
- Delete Property
- Owner-specific Dashboard

## 🤖 AI Property Description Generator
Generate professional real-estate descriptions instantly using Google Gemini AI.

The generator accepts:

- Property Title
- Location
- Price per Night
- Bedrooms
- Bathrooms
- Property Type
- Amenities
- Additional Attractions

and returns a polished, marketing-friendly description ready for publishing.

## 🎨 Frontend
- Responsive UI
- Tailwind CSS
- React Router
- Loading States
- Error Handling
- Toast Notifications

## ⚙ Backend
- REST API
- Express.js
- MongoDB Atlas
- Mongoose ODM
- Input Validation
- Error Middleware
- Rate Limiting
- CORS Configuration

---

# 🛠 Tech Stack

## Frontend

- React
- Vite
- Tailwind CSS
- React Router DOM
- Axios

## Backend

- Node.js
- Express.js

## Database

- MongoDB Atlas
- Mongoose

## Authentication

- JWT
- Google OAuth 2.0
- Passport.js

## AI

- Google Gemini API
- @google/generative-ai SDK

## Deployment

- Frontend → Vercel
- Backend → Render
- Database → MongoDB Atlas

---

# 📂 Project Structure

```text
homeStay/
│
├── assets/
│   └── DatabaseSchema.png
│
├── public/
│
├── src/
│   ├── assets/
│   ├── components/
│   ├── layouts/
│   ├── pages/
│   ├── routes/
│   ├── services/
│   ├── context/
│   └── utils/
│
├── backend/
│   ├── config/
│   ├── controllers/
│   ├── middleware/
│   ├── models/
│   ├── routes/
│   ├── services/
│   ├── data/
│   ├── server.js
│   ├── seed.js
│   ├── package.json
│   └── .env.example
│
├── README.md
└── PROMPTS.md
```

---

# 🚀 Installation

Clone the repository

```bash
git clone https://github.com/NainaKharola/homeStay.git
```

Move into the project directory

```bash
cd homeStay
```

---

# 💻 Frontend Setup

Install dependencies

```bash
npm install
```

Run the frontend

```bash
npm run dev
```

Frontend will run at

```text
http://localhost:5173
```

---

# 🖥 Backend Setup

Navigate to backend

```bash
cd backend
```

Install dependencies

```bash
npm install
```

Create a `.env` file

```env
PORT=5000
MONGODB_URI=your_mongodb_connection_string
JWT_SECRET=your_secret_key

CLIENT_URL=http://localhost:5173
FRONTEND_URL=https://home-stay-liard-ten.vercel.app

GOOGLE_CLIENT_ID=your_google_client_id
GOOGLE_CLIENT_SECRET=your_google_client_secret

CALLBACK_URL=http://localhost:5000/api/auth/google/callback
GOOGLE_CALLBACK_URL=http://localhost:5000/api/auth/google/callback

GEMINI_API_KEY=your_google_gemini_api_key
```

Run backend

```bash
npm run dev
```

or

```bash
npm start
```

Backend runs on

```text
http://localhost:5000
```

---

# 🌐 Live Demo

### Frontend

https://home-stay-liard-ten.vercel.app/

### Backend

https://homestay-mni0.onrender.com/

---

# 🗄 Database

The application uses **MongoDB Atlas** as its cloud-hosted database.

### Collections

- Users
- Properties
- Bookings (Planned)

### Features

- Cloud Database
- Persistent Storage
- Mongoose Validation
- CRUD Operations
- Environment Variable Support

---

# 🗂 Database Schema

### Collections

- User
- Property
- Booking

### Relationships

- One User can own multiple Properties.
- One User can create multiple Bookings.
- One Property can have multiple Bookings.

![Database Schema](assets/DatabaseSchema.png)

---

# 🤖 AI Property Description Generator

The AI Property Description Generator helps hosts write attractive and professional property listings in seconds.

### Features

- Generates marketing-friendly descriptions
- Uses Google Gemini AI
- Accepts property details as input
- Clean single-paragraph output
- One-click integration into property form

### Inputs

- Title
- Location
- Price
- Bedrooms
- Bathrooms
- Property Type
- Amenities
- Additional Attractions

---

# 🔑 Generate a Google Gemini API Key

1. Visit

https://aistudio.google.com/

2. Login with your Google account.

3. Click

```
Get API Key
```

4. Create a new API key.

5. Add it inside

```env
backend/.env
```

```env
GEMINI_API_KEY=your_api_key
```

---

# 📡 REST API Endpoints

| Method | Endpoint | Access | Description |
|---------|----------|--------|-------------|
| POST | `/api/auth/register` | Public | Register User |
| POST | `/api/auth/login` | Public | Login User |
| GET | `/api/auth/google` | Public | Google OAuth Login |
| GET | `/api/auth/google/callback` | Public | Google Callback |
| GET | `/api/auth/me` | Private | Logged-in User |
| GET | `/api/properties` | Public | Get All Properties |
| GET | `/api/properties/:id` | Public | Property Details |
| POST | `/api/properties` | Private | Create Property |
| PUT | `/api/properties/:id` | Private | Update Property |
| DELETE | `/api/properties/:id` | Private | Delete Property |
| POST | `/api/ai/property-description` | Private | Generate AI Description |

---

# 🔒 Environment Variables

```env
PORT=5000

MONGODB_URI=your_connection_string

JWT_SECRET=your_secret

CLIENT_URL=http://localhost:5173

FRONTEND_URL=https://home-stay-liard-ten.vercel.app

GOOGLE_CLIENT_ID=your_client_id

GOOGLE_CLIENT_SECRET=your_client_secret

CALLBACK_URL=http://localhost:5000/api/auth/google/callback

GOOGLE_CALLBACK_URL=http://localhost:5000/api/auth/google/callback

GEMINI_API_KEY=your_gemini_api_key
```

> **Note:** Never commit your `.env` file or API keys to GitHub.

---

# 📖 Prompt Engineering

The prompt engineering process for the AI Property Description Generator is documented in:

```
PROMPTS.md
```

The document contains:

- Prompt Version 1
- Prompt Version 2
- Prompt Version 3
- Testing Results
- Prompt Improvements
- Final Prompt
- Deployment Notes

---

# 📸 Screenshots

You can include screenshots here.

Example:

```
screenshots/
│
├── home.png
├── dashboard.png
├── login.png
├── ai-generator.png
├── property-details.png
```

Then display them like:

```markdown
## Home Page

![Home](screenshots/home.png)

## Dashboard

![Dashboard](screenshots/dashboard.png)

## AI Generator

![AI](screenshots/ai-generator.png)
```

---

# Live Deployment

## Frontend

https://home-stay-liard-ten.vercel.app/

## Backend

https://homestay-mni0.onrender.com/

---

## Known Limitations

- The backend is hosted on Render's free tier.
- After approximately 15 minutes of inactivity, the backend enters sleep mode.
- The first request after inactivity may take 30–60 seconds while the service wakes up.
- Subsequent requests are processed normally.

# 👩‍💻 Author

**Naina Kharola**

B.Tech Computer Science Engineering

AI-Assisted Full Stack Web Development Internship

---

# 📄 License

This project was developed for educational and internship purposes.