# Ecommerce API with FastAPI

An **Ecommerce API** built with **FastAPI**, PostgreSQL, and JWT authentication for secure, scalable, and efficient backend operations.

This API provides comprehensive features for managing products, categories, users, and shopping carts, with built-in search, filtering, and account management functionality.

---

## Overview

This Ecommerce API is designed to provide a **full backend solution** for online stores. Key objectives include:

* Scalable and maintainable code architecture.
* Fast API response times leveraging **FastAPI** async capabilities.
* Secure authentication and authorization using **JWT**.
* Easy integration with frontend applications (React, Vue, etc.).
* Complete API documentation with **Swagger UI** and **ReDoc**.

### Example Endpoint Usage

```python
# Fetch all products
import requests

response = requests.get("http://127.0.0.1:8000/products/")
print(response.json())

# Authenticate a user
login_data = {"email": "user@example.com", "password": "securepassword"}
response = requests.post("http://127.0.0.1:8000/auth/login/", json=login_data)
access_token = response.json()["access_token"]
```

---

## Technical Highlights

* **FastAPI for High Performance:** Built on top of Starlette, FastAPI provides **async-first** performance and automatic data validation with **Pydantic**.
* **JWT Authentication:** Secure user login with **access and refresh tokens**, supporting fine-grained authorization.
* **Database Integration:** PostgreSQL with **SQLAlchemy ORM** for structured and reliable data storage.
* **Real-time Features:** Optionally integrated with **Supabase** for real-time updates and authentication.
* **Comprehensive CRUD Operations:** Products, categories, and users can be **created, read, updated, and deleted** easily.
* **Advanced Search & Filtering:** Users can filter and search products efficiently for better UX.
* **Documentation-Ready:** Full API documentation available via Swagger UI and ReDoc.

```python
# Example Product CRUD with FastAPI
from fastapi import FastAPI, HTTPException
from models import Product, ProductCreate
from database import SessionLocal

app = FastAPI()

@app.post("/products/")
def create_product(product: ProductCreate):
    db = SessionLocal()
    db_product = Product(**product.dict())
    db.add(db_product)
    db.commit()
    db.refresh(db_product)
    return db_product
```

---

## Demo

* **Source Code:** [GitHub Repository](https://github.com/boluwatife-py/E-commerce-backend-fastapi-python)
* **Live API Testing:** Swagger UI at `/docs` and ReDoc at `/redoc` when running locally.

---

## Features

* **Product Management:** CRUD operations for products with detailed metadata.
* **Category Management:** CRUD operations for product categories.
* **User Management:** Admin-only and user-specific endpoints.
* **Authentication:** Sign-up, login, JWT-based access and refresh tokens.
* **Cart Management:** Add, remove, update cart items.
* **Search & Filter:** Advanced search by product attributes and categories.
* **Account Management:** Users can view, update, or delete their accounts.
* **API Documentation:** Auto-generated via FastAPI (`/docs` & `/redoc`).

---

## Technologies Used

* **FastAPI** – Modern Python web framework.
* **PostgreSQL** – Relational database system.
* **Supabase** – Real-time database and auth backend.
* **SQLAlchemy** – ORM for database operations.
* **Pydantic** – Data validation and serialization.
* **Uvicorn** – ASGI server for running FastAPI apps.
* **JWT** – Secure authentication.

---

## API Endpoints (Highlights)

| Endpoint          | Method | Description                       | User Type |
| ----------------- | ------ | --------------------------------- | --------- |
| `/products/`      | GET    | List all products                 | User      |
| `/products/`      | POST   | Create a new product              | Admin     |
| `/products/{id}/` | GET    | Retrieve product details          | User      |
| `/auth/signup/`   | POST   | Register new user                 | User      |
| `/auth/login/`    | POST   | Authenticate and generate tokens  | User      |
| `/auth/refresh/`  | POST   | Refresh access token              | User      |
| `/account/`       | GET    | Get authenticated user info       | User      |
| `/account/`       | PUT    | Update authenticated user info    | User      |
| `/account/`       | DELETE | Remove authenticated user account | User      |

> Full API endpoints available in the [GitHub README](https://github.com/boluwatife-py/E-commerce-backend-fastapi-python).

---

## Installation

```bash
# Clone repository
git clone https://github.com/boluwatife-py/E-commerce-backend-fastapi-python.git
cd E-commerce-backend-fastapi-python

# Create virtual environment
python3 -m venv venv
source venv/bin/activate   # Linux/macOS
venv\Scripts\activate      # Windows

# Install dependencies
pip install -r requirements.txt
```

---

## Usage

```bash
# Run database migrations
python migrate.py

# Start FastAPI server
python run.py

# Access documentation
# Swagger UI: http://127.0.0.1:8000/docs/
# ReDoc: http://127.0.0.1:8000/redoc/
```

---

## Contributing

* Fork the repository
* Create your branch: `git checkout -b feature-name`
* Make changes and commit: `git commit -m 'Add new feature'`
* Push to branch: `git push origin feature-name`
* Open a pull request

---

## License

This project is licensed under the [MIT License](LICENSE).

---
