# Planetary API

A comprehensive RESTful API for managing planetary data with user authentication and email functionality. Built with Flask, this API allows users to register, login, and perform CRUD operations on planetary information with JWT-based security.

## 🚀 Features

- **User Authentication**: Register, login, and JWT token-based authorization
- **Planetary CRUD**: Complete Create, Read, Update, Delete operations for planets
- **Email Integration**: Password recovery via email using Mailtrap
- **Database Seeding**: Pre-populated with Mercury, Venus, and Earth data
- **Protected Endpoints**: JWT required for modifying data
- **CLI Commands**: Custom commands for database management

## 🛠️ Technologies Used

- **Flask** - Web framework
- **SQLAlchemy** - ORM for database operations
- **Flask-JWT-Extended** - JWT authentication
- **Flask-Marshmallow** - Object serialization/deserialization
- **Flask-Mail** - Email functionality
- **SQLite** - Development database
- **Python 3.8+** - Programming language

## 📋 Prerequisites

- Python 3.8 or higher
- pip (Python package manager)
- Mailtrap account (for email testing)

## 🔧 Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/yourusername/planetary-api.git
   cd planetary-api
   ```

2. **Create a virtual environment**
   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   ```

3. **Install dependencies**
   ```bash
   pip install -r requirements.txt
   ```

4. **Configure environment variables** (optional)
   Edit `app.py` to update:
   - JWT secret key
   - Mailtrap credentials
   - Database URI

5. **Create the database**
   ```bash
   flask db_create
   ```

6. **Seed the database with initial data**
   ```bash
   flask db_seed
   ```

7. **Run the application**
   ```bash
   python app.py
   ```

8. **Access the API** at http://localhost:5000

## 📚 API Endpoints

| Method | Endpoint | Description | Authentication |
|--------|----------|-------------|----------------|
| GET | `/` | Welcome message | None |
| GET | `/super_simple` | Simple test endpoint | None |
| GET | `/planets` | Get all planets | None |
| GET | `/planet_details/<int:planet_id>` | Get specific planet | None |
| POST | `/register` | Register new user | None |
| POST | `/login` | User login | None |
| GET | `/retrieve_password/<string:email>` | Recover password via email | None |
| POST | `/add_planet` | Add new planet | JWT Required |
| PUT | `/update_planet` | Update planet | JWT Required |
| DELETE | `/remove_planet/<int:planet_id>` | Delete planet | JWT Required |
| GET | `/parameters` | Query parameter example | None |
| GET | `/url_variables/<string:name>/<int:age>` | URL variable example | None |

## 📝 Request/Response Examples

### Register a New User
```bash
POST http://localhost:5000/register
Content-Type: application/x-www-form-urlencoded

email=newuser@example.com
first_name=John
last_name=Doe
password=securepassword123
```

### Login
```bash
POST http://localhost:5000/login
Content-Type: application/json

{
    "email": "test@test.com",
    "password": "P@ssw0rd"
}
```

Response:
```json
{
    "access_token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...",
    "message": "Login Succeeded!"
}
```

### Add a Planet (Authenticated)
```bash
POST http://localhost:5000/add_planet
Authorization: Bearer <your_jwt_token>
Content-Type: application/x-www-form-urlencoded

planet_name=Mars
planet_type=Class M
home_star=Sol
mass=6.39e23
radius=2106
distance=141.6e6
```

### Get All Planets
```bash
GET http://localhost:5000/planets
```

### Update a Planet (Authenticated)
```bash
PUT http://localhost:5000/update_planet
Authorization: Bearer <your_jwt_token>
Content-Type: application/x-www-form-urlencoded

planet_id=1
planet_name=Mercury
planet_type=Class D
home_star=Sol
mass=3.285e23
radius=1516
distance=35.98e6
```

## 🗄️ Database Schema

### Users Table
| Column | Type | Description |
|--------|------|-------------|
| id | Integer | Primary key |
| first_name | String | User's first name |
| last_name | String | User's last name |
| email | String | Unique email address |
| password | String | User password |

### Planets Table
| Column | Type | Description |
|--------|------|-------------|
| planet_id | Integer | Primary key |
| planet_name | String | Name of the planet |
| planet_type | String | Classification (Class D, K, M, etc.) |
| home_star | String | Parent star system |
| mass | Float | Planetary mass |
| radius | Float | Planetary radius |
| distance | Float | Distance from home star |

## 🛠️ CLI Commands

| Command | Description |
|---------|-------------|
| `flask db_create` | Create all database tables |
| `flask db_drop` | Drop all database tables |
| `flask db_seed` | Seed database with initial data |

## 📁 Project Structure

```
planetary-api/
│
├── app.py                 # Main application file
├── requirements.txt       # Project dependencies
└── planets.db            # SQLite database (created after setup)
```

## 🔐 Security Features

- JWT tokens for authenticated endpoints
- Password protection (though currently stored as plaintext - should be hashed in production)
- Email verification for password recovery

## 🚦 Testing the API

You can test the API using:
- **Browser**: For GET requests
- **Postman**: For all HTTP methods including authenticated requests
- **cURL**: Command-line testing

Example authenticated request with cURL:
```bash
curl -X POST http://localhost:5000/add_planet \
  -H "Authorization: Bearer <your_token>" \
  -d "planet_name=Jupiter&planet_type=Class J&home_star=Sol&mass=1.898e27&radius=43441&distance=484e6"
```

## 💡 Future Improvements

- Implement password hashing (bcrypt)
- Add input validation
- Create comprehensive test suite
- Add pagination for planet listing
- Implement refresh tokens
- Add user roles and permissions
- Deploy to cloud platform

## ⚠️ Important Notes for Production

- Change the JWT secret key to a secure value
- Use environment variables for sensitive data
- Replace Mailtrap with a production email service
- Switch to PostgreSQL or MySQL for production
- Implement proper password hashing
- Add rate limiting
- Enable HTTPS

## 📄 License

This project is for educational purposes as part of a portfolio.

## 👨‍💻 Author

Matheesha Thamel

## 🙏 Acknowledgments

- Flask documentation
- SQLAlchemy documentation
- JWT Extended documentation
- Mailtrap for email testing services
