# Product Inventory Management API

A robust RESTful API backend for product inventory management built with FastAPI and SQLAlchemy. This project provides a complete CRUD interface for managing product data with PostgreSQL database integration.

## 🚀 Features

- **Full CRUD Operations**: Create, Read, Update, and Delete products
- **Automatic Database Setup**: Creates tables and seeds initial product data
- **Data Validation**: Pydantic models for request/response validation
- **Dependency Injection**: Clean database session management
- **RESTful Endpoints**: Well-structured API endpoints following REST conventions

## 🛠️ Technologies Used

- **FastAPI** - Modern web framework for building APIs
- **SQLAlchemy** - SQL toolkit and ORM
- **PostgreSQL** - Relational database
- **Pydantic** - Data validation using Python type hints
- **Python 3.8+** - Programming language

## 📋 Prerequisites

- Python 3.8 or higher
- PostgreSQL installed and running
- pip (Python package manager)

## 🔧 Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/yourusername/product-inventory-api.git
   cd product-inventory-api
   ```

2. **Create a virtual environment**
   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   ```

3. **Install dependencies**
   ```bash
   pip install fastapi uvicorn sqlalchemy psycopg2-binary pydantic
   ```

4. **Configure PostgreSQL**
   - Create a PostgreSQL database named `Telusko`
   - Update the database URL in `database.py` if needed:
     ```python
     db_url = "postgresql://postgres:matheesha@localhost:5432/Telusko"
     ```

5. **Run the application**
   ```bash
   uvicorn main:app --reload
   ```

6. **Access the API**
   - API: http://localhost:8000
   - Interactive docs: http://localhost:8000/docs
   - Alternative docs: http://localhost:8000/redoc

## 📚 API Endpoints

| Method | Endpoint | Description | Authentication |
|--------|----------|-------------|----------------|
| GET | `/` | Welcome message | None |
| GET | `/products` | Get all products | None |
| GET | `/product/{product_id}` | Get a specific product | None |
| POST | `/products` | Add a new product | None |
| PUT | `/product` | Update an existing product | None |
| DELETE | `/product` | Delete a product | None |

## 📝 Request/Response Examples

### Get All Products
```bash
GET http://localhost:8000/products
```

### Add a New Product
```bash
POST http://localhost:8000/products
Content-Type: application/json

{
    "id": 5,
    "name": "Tablet",
    "description": "10-inch Android tablet",
    "price": 299.99
}
```

### Update a Product
```bash
PUT http://localhost:8000/product?id=1
Content-Type: application/json

{
    "id": 1,
    "name": "Gaming Laptop",
    "description": "High performance gaming laptop with RTX graphics",
    "price": 1500.00
}
```

### Delete a Product
```bash
DELETE http://localhost:8000/product?id=3
```

## 🗄️ Database Schema

### Products Table
| Column | Type | Description |
|--------|------|-------------|
| id | Integer | Primary key, auto-incrementing |
| name | String | Product name |
| description | String | Product description |
| price | Float | Product price |

## 📁 Project Structure

```
product-inventory-api/
│
├── main.py              # FastAPI application and endpoints
├── database.py          # Database connection configuration
├── database_models.py   # SQLAlchemy ORM models
├── models.py           # Pydantic models for validation
└── requirements.txt    # Project dependencies
```

## 🚦 Running Tests

Currently, no test suite is implemented. You can test the API using:
- Browser for GET requests
- Postman or similar tools for all methods
- Swagger UI at http://localhost:8000/docs

## 💡 Future Improvements

- Add user authentication and authorization
- Implement pagination for product listing
- Add search and filter functionality
- Create comprehensive test suite
- Add input validation and error handling
- Implement logging

## 📄 License

This project is for educational purposes as part of a portfolio.

## 👨‍💻 Author

[Your Name]

## 🙏 Acknowledgments

- FastAPI documentation
- SQLAlchemy documentation
- Telusko tutorials for inspiration
