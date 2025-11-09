# qr-menu-project-backend

This backend project provides the API and data management for a QR code-based menu system. It allows restaurants and cafes to easily manage their menus online and display them to customers via QR codes.

## Key Features & Benefits

*   **Menu Management:** Create, update, and delete menu items with details like name, description, price, and availability.
*   **Category Organization:** Organize menu items into categories for easy browsing.
*   **Database Persistence:** Uses a PostgreSQL database to store menu data securely.
*   **API Endpoints:** Provides a RESTful API for accessing and managing menu data.
*   **Authentication:** Includes JWT-based authentication for secure access to administrative functions.
*   **Dockerized Deployment:** Easily deployable using Docker for consistent environments.
*   **Database Migrations:** Uses database migrations for schema management.

## Prerequisites & Dependencies

*   **Go:** Version 1.22 or higher
*   **Docker:** Docker installed and running on your machine
*   **Docker Compose:** Docker Compose installed on your machine
*   **PostgreSQL:** A PostgreSQL database instance

## Installation & Setup Instructions

1.  **Clone the Repository:**

    ```bash
    git clone git@github.com:HazarBakir/qr-menu-project-backend.git
    cd qr-menu-project-backend
    ```

2.  **Configure Environment Variables:**

    Create a `.env` file (or configure environment variables directly) with the following information:

    ```
    DATABASE_URL="postgres://user:password@host:port/dbname" # Replace with your PostgreSQL connection string
    JWT_SECRET="your-secret-key" # Replace with a strong secret key
    ```

3.  **Run Database Migrations:**

    Use the provided `Makefile` to run database migrations. This will create the necessary tables in your PostgreSQL database.

    ```bash
    make migrateup
    ```

4.  **Build and Run the Application with Docker Compose:**

    Use Docker Compose to build and run the application.

    ```bash
    docker-compose up --build
    ```

    This will build the Docker image and start the container, exposing the application on the specified port (e.g., `8080`).

## Usage Examples & API Documentation

The API provides endpoints for managing menus, categories, and users. Here are a few example requests:

*   **Get all menu items:**

    `GET /api/menu-items`

*   **Create a new menu item:**

    `POST /api/menu-items`

    ```json
    {
      "name": "Example Dish",
      "description": "A delicious example dish",
      "price": 10.99,
      "category_id": 1
    }
    ```

*   **Update a menu item:**

    `PUT /api/menu-items/{id}`

    ```json
    {
      "name": "Updated Dish Name",
      "price": 12.99
    }
    ```

*   **Delete a menu item:**

    `DELETE /api/menu-items/{id}`

*   **Authentication (Login):**

    `POST /api/auth/login`

    ```json
    {
      "username": "your_username",
      "password": "your_password"
    }
    ```

    This endpoint returns a JWT token that you'll need to include in the `Authorization` header of subsequent requests requiring authentication (e.g., creating, updating, and deleting menu items). The header should be in the format: `Authorization: Bearer <token>`.

    **Note:** Replace placeholders like `{id}`, `your_username`, and `your_password` with actual values.  Comprehensive API documentation (e.g., using Swagger/OpenAPI) would be beneficial for detailed endpoint information.

## Configuration Options

*   **`DATABASE_URL`:**  The connection string for the PostgreSQL database.  This is required for the application to connect to your database.
*   **`JWT_SECRET`:** The secret key used to sign JWT tokens.  **Important:** Use a strong, randomly generated secret key in a production environment.
*   **`PORT`:** The port on which the application listens for incoming requests.  Defaults to `8080` if not specified.

These configuration options can be set as environment variables or within a `.env` file.

## Contributing Guidelines

We welcome contributions to this project! To contribute:

1.  Fork the repository.
2.  Create a new branch for your feature or bug fix.
3.  Make your changes and commit them with clear, descriptive commit messages.
4.  Submit a pull request with a detailed explanation of your changes.

Please follow the existing code style and conventions. Ensure that your code is well-tested.

## License Information

This project has no specific license specified. All rights are reserved by the owner.

## Acknowledgments

*   [Echo](https://echo.labstack.com/): For providing a lightweight and efficient web framework.
*   [GORM](https://gorm.io/): For simplifying database interactions.
*   [golang-jwt/jwt](https://github.com/golang-jwt/jwt): For providing JWT support.
