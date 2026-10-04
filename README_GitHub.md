# 🌦️ AI WeatherWise API

A RESTful backend application built with **Node.js, Express.js, MongoDB, and Mongoose**. AI WeatherWise provides secure user authentication, favorite-location management, real-time weather information, and AI-powered weather insights using Google Gemini.

## ✨ Features

- 🔐 **User Authentication**
  - User registration and login
  - Password hashing with `bcryptjs`
  - JWT-based authorization
  - Protected profile endpoint

- 📍 **Favorite Locations**
  - Add favorite locations
  - View saved locations
  - Update locations
  - Delete locations

- 🌤️ **Current Weather**
  - Temperature
  - Humidity
  - Wind speed
  - Weather condition
  - OpenWeatherMap integration

- 🤖 **AI Weather Insights**
  - AI-generated weather summaries
  - Personalized recommendations
  - Clothing, hydration, and activity suggestions
  - Google Gemini integration

- 🛡️ **Fallback Mode**
  - Works with deterministic mock responses when OpenWeatherMap or Gemini API keys are not configured.
  - Makes the project easier to test locally.

## 🛠️ Technology Stack

| Technology | Purpose |
|---|---|
| Node.js | Runtime environment |
| Express.js | Web framework |
| MongoDB | Database |
| Mongoose | MongoDB ODM |
| JWT | Authentication |
| bcryptjs | Password hashing |
| OpenWeatherMap API | Weather data |
| Google Gemini API | AI weather insights |

## 📁 Project Structure

```text
src/
├── config/
│   └── db.js
├── models/
│   ├── User.js
│   └── Location.js
├── middleware/
│   └── authMiddleware.js
├── controllers/
│   ├── authController.js
│   ├── locationController.js
│   ├── weatherController.js
│   └── aiController.js
├── routes/
│   ├── authRoutes.js
│   ├── locationRoutes.js
│   ├── weatherRoutes.js
│   └── aiRoutes.js
├── services/
│   ├── weatherService.js
│   └── aiService.js
├── app.js
└── server.js
```

## 🚀 Getting Started

### Prerequisites

Make sure you have the following installed:

- [Node.js](https://nodejs.org/) v18 or later
- npm
- MongoDB or a MongoDB Atlas account
- Postman (optional, for API testing)

### 1. Clone the Repository

```bash
git clone <YOUR_GITHUB_REPOSITORY_URL>
cd <YOUR_PROJECT_FOLDER>
```

### 2. Install Dependencies

```bash
npm install
```

### 3. Configure Environment Variables

Create a `.env` file in the project root:

```env
PORT=5000
MONGO_URI=mongodb://127.0.0.1:27017/weatherwise
JWT_SECRET=your_super_secret_jwt_key
OPENWEATHER_API_KEY=your_openweathermap_api_key
GEMINI_API_KEY=your_gemini_api_key
```

> ⚠️ **Security:** Never upload your real `.env` file or API keys to GitHub.

Add `.env` to your `.gitignore` file:

```gitignore
node_modules/
.env
```

If API keys are not configured, the application can use its built-in fallback responses for testing.

### 4. Start the Application

Development mode:

```bash
npm run dev
```

Production mode:

```bash
npm start
```

The server runs at:

```text
http://localhost:5000
```

## 📡 API Documentation

### 1. Authentication

| Endpoint | Method | Access | Description |
|---|---|---|---|
| `/api/auth/register` | POST | Public | Register a new user and receive a JWT token |
| `/api/auth/login` | POST | Public | Log in and receive a JWT token |
| `/api/auth/profile` | GET | Private | Get the logged-in user's profile |

### 2. Favorite Locations

| Endpoint | Method | Access | Description |
|---|---|---|---|
| `/api/locations` | POST | Private | Add a favorite city |
| `/api/locations` | GET | Private | Get all favorite cities |
| `/api/locations/:id` | PUT | Private | Update a favorite city |
| `/api/locations/:id` | DELETE | Private | Delete a favorite city |

### 3. Weather

| Endpoint | Method | Access | Description |
|---|---|---|---|
| `/api/weather/:city` | GET | Public | Get current weather information for a city |

### 4. AI Weather Insights

| Endpoint | Method | Access | Description |
|---|---|---|---|
| `/api/ai/weather-summary` | POST | Private | Generate an AI weather summary |
| `/api/ai/weather-recommendation` | POST | Private | Generate personalized weather recommendations |

## 🧪 API Testing with Postman

To test the API:

1. Open Postman.
2. Import `postman_collection.json` from the project root.
3. Register a new user.
4. Log in to receive a JWT token.
5. Test the protected endpoints using the saved token.
6. Test location, weather, and AI endpoints.

The Postman collection can automatically store the JWT token in the collection variable `token`.

## 🔒 Authentication

Private endpoints require a valid JWT token.

Use the following authorization header:

```http
Authorization: Bearer <YOUR_JWT_TOKEN>
```

## 📌 Example Request

### Get Weather

```http
GET /api/weather/Chennai
```

Example response:

```json
{
  "city": "Chennai",
  "temperature": 30,
  "humidity": 70,
  "windSpeed": 12,
  "condition": "Clear"
}
```

## 🤖 AI Weather Recommendation

Example request:

```json
{
  "temperature": 30,
  "condition": "Clear"
}
```

The API generates recommendations such as suitable clothing, hydration advice, and activity suggestions.

## 🌐 Project Purpose

AI WeatherWise combines real-time weather information with artificial intelligence to provide users with useful, personalized weather guidance through a simple REST API.

## 👩‍💻 Author

**Umme Asfa Khanam**

BCA Student

## 📄 License

This project is created for educational and project purposes.
