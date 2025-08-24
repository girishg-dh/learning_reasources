
# Python Model Protocol Server with FastAPI and PostgreSQL

This project provides a simple and extensible model protocol server built with Python, FastAPI, and SQLAlchemy for interacting with a PostgreSQL database.

## Features

- **FastAPI:** A modern, high-performance web framework for building APIs.
- **SQLAlchemy:** A powerful SQL toolkit and Object-Relational Mapper (ORM).
- **PostgreSQL:** A robust, open-source object-relational database system.
- **CRUD Operations:** Full support for Create, Read, Update, and Delete operations on a `Task` model.
- **Pydantic:** Data validation and settings management using Python type annotations.

## Installation

1.  **Clone the repository (or download the files).**

2.  **Create and activate a virtual environment:**

    ```bash
    python3 -m venv venv
    source venv/bin/activate
    ```

3.  **Install the required dependencies:**

    ```bash
    pip install -r requirements.txt
    ```

## Configuration

The database connection URL is configured via the `DATABASE_URL` environment variable. If not set, it defaults to `postgresql://user:password@localhost/mydatabase`.

Before running the server, export the `DATABASE_URL` with your PostgreSQL connection details:

```bash
export DATABASE_URL="postgresql://YOUR_USER:YOUR_PASSWORD@YOUR_HOST:YOUR_PORT/YOUR_DATABASE"
```

## Running the Server

To run the server, use the following command:

```bash
uvicorn server:app --reload
```

The server will be available at `http://127.0.0.1:8000`.

## API Endpoints

### Create a Task

- **POST** `/tasks/`

- **Request Body:**

  ```json
  {
    "title": "My First Task",
    "description": "This is a description of my first task.",
    "completed": false
  }
  ```

- **Example:**

  ```bash
  curl -X POST -H "Content-Type: application/json" -d '{
    "title": "My First Task",
    "description": "This is a description of my first task.",
    "completed": false
  }' http://127.0.0.1:8000/tasks/
  ```

### Get All Tasks

- **GET** `/tasks/`

- **Example:**

  ```bash
  curl http://127.0.0.1:8000/tasks/
  ```

### Get a Single Task

- **GET** `/tasks/{task_id}`

- **Example:**

  ```bash
  curl http://127.0.0.1:8000/tasks/1
  ```

### Update a Task

- **PUT** `/tasks/{task_id}`

- **Request Body:**

  ```json
  {
    "title": "Updated Task Title",
    "description": "Updated description.",
    "completed": true
  }
  ```

- **Example:**

  ```bash
  curl -X PUT -H "Content-Type: application/json" -d '{
    "title": "Updated Task Title",
    "description": "Updated description.",
    "completed": true
  }' http://127.0.0.1:8000/tasks/1
  ```

### Delete a Task

- **DELETE** `/tasks/{task_id}`

- **Example:**

  ```bash
  curl -X DELETE http://127.0.0.1:8000/tasks/1
  ```
