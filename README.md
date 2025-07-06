
# User Authentication & News Preferences API

This Spring Boot application provides a RESTful API for user registration, login, email verification, and news preferences management. It also integrates with a news service to fetch articles for authenticated users.

---

## 🚀 Features

- ✅ User registration with token-based verification
- ✅ JWT-based login system
- ✅ Role-based access control using Spring Security
- ✅ User preference management
- ✅ News feed for authenticated users
- ✅ Reactive support via Project Reactor (`Mono`)

---

## 🛠️ Tech Stack

- Java 17+
- Spring Boot
- Spring Security
- Project Reactor (WebFlux)
- Gradle
- JWT (for authentication)
- (Optional) PostgreSQL / H2 (for persistence)

---

## 📦 API Endpoints

### 🔐 Authentication

#### `POST /register`
Registers a new user and generates a verification token.

**Request Body:**
```json
{
  "email": "user@example.com",
  "password": "securePass123",
  "name": "John Doe"
}
```

**Response:**
```json
{
  "id": 1,
  "email": "user@example.com",
  "name": "John Doe",
  "enabled": false
}
```

---

#### `POST /verifyRegistration?token=...`
Verifies the user's registration using the token sent in `/register`.

**Response:**
- `"User registration verified successfully."` if valid
- `"Invalid or expired token."` if not

---

#### `POST /signin`
Logs in a user and returns a JWT token.

**Params:**
- `username`
- `password`

**Response:**
```
<JWT Token or Success Message>
```

---

### 👤 User Actions (Requires `ROLE_USER`)

#### `POST /test`
Test endpoint to verify authentication.

**Response:**
```
Test endpoint is working!
```

---

#### `GET /news`
Fetches personalized news articles for the authenticated user.

**Response:**
```json
[
  {
    "title": "Latest Tech News",
    "description": "Some summary...",
    "url": "https://example.com/article"
  }
]
```

---

#### `GET /preferences`
Fetches saved user preferences.

**Response:**
```json
[
  {
    "category": "Technology"
  }
]
```

---

#### `PUT /preferences`
Updates the user's news preferences.

**Request Body:**
```json
[
  { "category": "Technology" },
  { "category": "Sports" }
]
```

**Response:**
```json
[
  { "category": "Technology" },
  { "category": "Sports" }
]
```

---



