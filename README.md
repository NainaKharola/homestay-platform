# 🏡 HomeStay

A full-stack homestay management and discovery platform with an AI-powered property description generator.

---

## 🌐 Live Demo

**Frontend:**  
https://home-stay-liard-ten.vercel.app/

**Backend:**  
https://homestay-mni0.onrender.com/

---


# ✨ Features

## 👤 Authentication

- User registration using email and password
- User login using email and password
- Google OAuth 2.0 authentication
- JWT-based authentication
- Protected routes
- Persistent login session
- Logout functionality
- Authentication input validation
- Rate limiting for authentication endpoints

## 🏠 Property Management

- Create new homestay properties
- View all available properties
- View individual property details
- Search properties
- Update existing properties
- Delete properties
- Owner-specific property management
- Property information including:
  - Title
  - Location
  - Price per night
  - Bedrooms
  - Bathrooms
  - Property type
  - Amenities
  - Images
  - Description

## 🤖 AI Property Description Generator

HomeStay includes an AI-powered property description generator using **Google Gemini**.

Hosts can provide:

- Property title
- Location
- Price per night
- Number of bedrooms
- Number of bathrooms
- Property type
- Amenities
- Additional attractions/information

The AI generates a professional, readable and marketing-friendly property description that can be used for the property listing.

## 🎨 User Interface

- Responsive React interface
- Desktop and mobile-friendly layout
- React Router navigation
- Loading states
- Error handling
- Toast notifications
- Clean property listing interface
- User dashboard
- Property management interface

## 🔐 Backend Security

- JWT authentication
- Protected API routes
- Password hashing using bcrypt
- Request validation
- CORS configuration
- Authentication rate limiting
- Centralized error handling

---

# 🛠 Tech Stack

| Layer | Technology | Purpose |
|---|---|---|
| Frontend | React | Component-based user interface |
| Build Tool | Vite | Fast frontend development and production builds |
| Styling | Tailwind CSS | Responsive and consistent UI styling |
| Routing | React Router DOM | Client-side navigation |
| Backend | Node.js | JavaScript runtime for server-side development |
| API Framework | Express.js | REST API development |
| Database | MongoDB Atlas | Cloud-based application data storage |
| ODM | Mongoose | MongoDB schema and database interaction |
| Authentication | JWT | Secure user authentication |
| OAuth | Google OAuth 2.0 + Passport.js | Google-based authentication |
| Password Security | bcrypt | Password hashing |
| AI | Google Gemini API | AI-generated property descriptions |
| Frontend Hosting | Vercel | Frontend deployment |
| Backend Hosting | Render | Backend/API deployment |

---

# 🚀 Setup Instructions

Follow the steps below to run HomeStay locally.

## 1. Clone the Repository

```bash
git clone https://github.com/NainaKharola/homeStay.git
```

Move into the project:

```bash
cd homeStay
```

---

# 💻 Frontend Setup

Install frontend dependencies:

```bash
npm install
```

Create a frontend environment file if required:

```text
.env
```

Example:

```env
VITE_BACKEND_URL=http://localhost:5000
VITE_API_URL=http://localhost:5000/api/auth
VITE_PROPERTIES_API_URL=http://localhost:5000/api/properties
VITE_AI_API_URL=http://localhost:5000/api/ai
```

Start the frontend:

```bash
npm run dev
```

The frontend will normally be available at:

```text
http://localhost:5173
```

---

# 🖥 Backend Setup

Open a new terminal and navigate to the backend:

```bash
cd backend
```

Install backend dependencies:

```bash
npm install
```

Create:

```text
backend/.env
```

Add the required environment variables:

```env
PORT=5000

MONGODB_URI=your_mongodb_connection_string

JWT_SECRET=your_jwt_secret

CLIENT_URL=http://localhost:5173
FRONTEND_URL=http://localhost:5173

GOOGLE_CLIENT_ID=your_google_client_id
GOOGLE_CLIENT_SECRET=your_google_client_secret

CALLBACK_URL=http://localhost:5000/api/auth/google/callback
GOOGLE_CALLBACK_URL=http://localhost:5000/api/auth/google/callback

GEMINI_API_KEY=your_gemini_api_key
```

Start the backend in development mode:

```bash
npm run dev
```

Or start it normally:

```bash
npm start
```

The backend will run at:

```text
http://localhost:5000
```

---

# 🔑 Environment Variables

## Frontend

```env
VITE_BACKEND_URL=
VITE_API_URL=
VITE_PROPERTIES_API_URL=
VITE_AI_API_URL=
```

## Backend

```env
PORT=
MONGODB_URI=
JWT_SECRET=

CLIENT_URL=
FRONTEND_URL=

GOOGLE_CLIENT_ID=
GOOGLE_CLIENT_SECRET=

CALLBACK_URL=
GOOGLE_CALLBACK_URL=

GEMINI_API_KEY=
```

### Security Note

Never commit:

```text
.env
```

or any API keys, database credentials, OAuth secrets or JWT secrets to GitHub.

Use `.env.example` files containing only placeholder values when sharing configuration examples.

---

# 📡 API Documentation

The backend exposes REST APIs through Express.js.

Base URL:

```text
https://homestay-mni0.onrender.com
```

---

## 🔐 Authentication APIs

### Register User

```http
POST /api/auth/register
```

Example request:

```json
{
  "name": "Naina Kharola",
  "email": "user@example.com",
  "password": "password123"
}
```

Purpose:

Creates a new HomeStay user account.

---

### Login User

```http
POST /api/auth/login
```

Example request:

```json
{
  "email": "user@example.com",
  "password": "password123"
}
```

Purpose:

Authenticates the user and returns authentication information.

---

### Get Current User

```http
GET /api/auth/me
```

Authentication:

```http
Authorization: Bearer <JWT_TOKEN>
```

Purpose:

Returns information about the currently authenticated user.

---

### Google Login

```http
GET /api/auth/google
```

Purpose:

Starts the Google OAuth 2.0 authentication flow.

---

# 🏠 Property APIs

### Get All Properties

```http
GET /api/properties
```

Example:

```text
https://homestay-mni0.onrender.com/api/properties
```

Example response:

```json
[
  {
    "id": 4,
    "title": "Forest Retreat",
    "location": "Coorg",
    "price": 2800,
    "rating": 4.5,
    "description": "Peaceful stay surrounded by nature."
  }
]
```

---

### Get Property by ID

```http
GET /api/properties/:id
```

Example:

```http
GET /api/properties/4
```

Purpose:

Returns details of a specific property.

---

### Search Properties

```http
GET /api/properties/search
```

Purpose:

Searches available properties based on supported search parameters.

---

### Create Property

```http
POST /api/properties
```

Authentication:

```http
Authorization: Bearer <JWT_TOKEN>
```

Example request:

```json
{
  "title": "Himalayan View",
  "location": "Nainital",
  "price": 2500,
  "bedrooms": 3,
  "bathrooms": 2,
  "propertyType": "Homestay",
  "amenities": [
    "Free WiFi",
    "Parking"
  ]
}
```

Purpose:

Creates a new property listing for the authenticated user.

---

### Update Property

```http
PUT /api/properties/:id
```

Authentication:

```http
Authorization: Bearer <JWT_TOKEN>
```

Purpose:

Updates an existing property owned by the authenticated user.

---

### Delete Property

```http
DELETE /api/properties/:id
```

Authentication:

```http
Authorization: Bearer <JWT_TOKEN>
```

Purpose:

Deletes an existing property listing.

---

# 🤖 AI API

## Generate Property Description

```http
POST /api/ai/property-description
```

Authentication:

```http
Authorization: Bearer <JWT_TOKEN>
```

The endpoint requires at least:

- Property title
- Property location

Example request:

```json
{
  "title": "Himalayan View",
  "location": "Nainital",
  "price": 2500,
  "bedrooms": 3,
  "bathrooms": 2,
  "propertyType": "Homestay",
  "amenities": [
    "Free WiFi",
    "Parking",
    "Mountain View"
  ],
  "additionalInfo": "Located close to Naini Lake."
}
```

Example response:

```json
{
  "success": true,
  "description": "A beautiful Himalayan retreat..."
}
```

The backend validates the required property information and sends a structured prompt to Google Gemini to generate the description.

---

# 🗄 Database

HomeStay uses **MongoDB Atlas** as its cloud-hosted database.

MongoDB was selected because:

- It provides flexible document-based storage.
- It integrates well with Node.js through Mongoose.
- Property data can contain different attributes.
- It provides persistent cloud storage.
- It supports scalable application development.

## Main Data Models

### User

Stores user authentication and profile information.

Typical information includes:

- Name
- Email
- Password hash
- Google authentication information where applicable

### Property

Stores homestay listing information.

Typical information includes:

- Property ID
- Title
- Location
- Price
- Rating
- Image
- Description
- Owner
- Creation timestamp
- Update timestamp

### Booking

The booking model/data structure is part of the planned application expansion.

---

# 🧩 Database Schema

The repository includes the database schema visualisation:

```text
assets/DatabaseSchema.png
```

![HomeStay Database Schema](assets/DatabaseSchema.png)

The main relationship is:

```text
User
  │
  └── owns
        │
        ▼
     Property
```

A user can own multiple property listings.

---

# 🏗 Architecture / Folder Structure

The project follows a separated frontend/backend architecture.

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
│   ├── context/
│   ├── layouts/
│   ├── pages/
│   ├── routes/
│   ├── services/
│   └── utils/
│
├── backend/
│   ├── config/
│   ├── controllers/
│   ├── data/
│   ├── middleware/
│   ├── models/
│   ├── routes/
│   ├── services/
│   ├── utils/
│   ├── server.js
│   ├── seed.js
│   ├── package.json
│   └── .env.example
│
├── README.md
└── PROMPTS.md
```

## Request Flow

```text
User
  │
  ▼
React + Vite Frontend
  │
  │ REST API
  ▼
Node.js + Express Backend
  │
  ├───────────────┐
  ▼               ▼
MongoDB Atlas    Google Gemini
```

---

# 🔒 Security

HomeStay implements several security measures:

- JWT-based authentication
- Protected backend routes
- bcrypt password hashing
- Request validation
- Authentication rate limiting
- CORS configuration
- Environment variables for secrets
- Centralized error handling

Authentication endpoints are rate-limited to help reduce repeated authentication attempts. 

---

# 🤖 AI Implementation

The AI feature is implemented through a dedicated backend route:

```text
POST /api/ai/property-description
```

The request is protected by authentication middleware.

The backend:

```text
Property Details
       ↓
Input Validation
       ↓
Prompt Builder
       ↓
Google Gemini
       ↓
Generated Description
       ↓
Frontend
```

The AI implementation uses:

```text
@google/generative-ai
```

and the Google Gemini API.

The prompt-engineering process is documented separately in:

```text
PROMPTS.md
```

---

# 📂 Important Project Files

| File / Folder | Purpose |
|---|---|
| `src/` | React frontend |
| `src/services/` | Frontend API services |
| `src/context/` | Application context and authentication state |
| `backend/server.js` | Express server entry point |
| `backend/routes/` | Backend API routes |
| `backend/controllers/` | Request handling logic |
| `backend/models/` | MongoDB/Mongoose models |
| `backend/services/` | External service integrations |
| `backend/middleware/` | Authentication and error middleware |
| `backend/utils/` | Utility functions and AI prompt building |
| `assets/DatabaseSchema.png` | Database schema |
| `PROMPTS.md` | AI prompt engineering documentation |

---

# ☁️ Deployment

## Frontend

The React/Vite frontend is deployed using **Vercel**.

Live URL:

https://home-stay-liard-ten.vercel.app/

## Backend

The Node.js/Express backend is deployed using **Render**.

Live URL:

https://homestay-mni0.onrender.com/

## Database

MongoDB Atlas is used as the cloud database.

## AI

Google Gemini API is used for AI-powered property description generation.

---

# ⚠️ Known Limitations

- The backend is hosted on Render's free tier.
- The backend may sleep after a period of inactivity.
- The first request after inactivity can therefore take longer while the service wakes up.
- The application currently focuses on property discovery and property management.
- Booking functionality can be expanded in future versions.
- AI-generated descriptions should still be reviewed by the property owner before publishing.
- Third-party services such as Google OAuth and Gemini require valid API credentials/configuration.

---

# 🔮 Future Improvements

Possible future improvements include:

- Complete booking and reservation functionality
- Payment integration
- Advanced property filtering
- Map-based property discovery
- Reviews and ratings
- Wishlist functionality
- More AI-assisted property features
- Improved analytics for property owners
- Notification and messaging functionality
- Additional deployment scalability

---

# 📖 Prompt Engineering

The AI prompt development process is documented in:

```text
PROMPTS.md
```

It contains:

- Initial prompt
- Prompt improvements
- Testing results
- Final prompt
- AI integration notes

---

# 🙌 Credits & Acknowledgements

HomeStay was developed as part of the **AI-Assisted Full Stack Web Development Internship at TBI-GEU**.

### Technologies & Services

- React
- Vite
- Tailwind CSS
- Node.js
- Express.js
- MongoDB Atlas
- Mongoose
- JWT
- Passport.js
- Google OAuth 2.0
- Google Gemini API
- Vercel
- Render

### Development Assistance

AI-assisted development tools were used during the development process for:

- Debugging
- Code improvement
- API troubleshooting
- Prompt engineering
- Documentation assistance

The project was independently integrated, tested and deployed as part of the internship capstone.

---

# 👩‍💻 Author

**Naina Kharola**

B.Tech Computer Science Engineering  
Graphic Era University

**Intern ID:** TBI-26100975

**Internship:** TBI-GEU AI-Assisted Full Stack Web Development Internship

---

# 📄 License

This project was developed for educational and internship purposes.
