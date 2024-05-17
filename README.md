GraphQL API with SQL Database in Docker

This project demonstrates how to create a GraphQL API using the Strawberry library with FastAPI, a SQL database, containerized with Docker, and run it on a local server. The setup provides a seamless way to develop and test GraphQL queries and mutations with a robust SQL database backend.

Table of Contents

Features
Prerequisites
Installation
Running the Project
Usage
Project Structure
Contributing
License
Features

GraphQL API for querying and mutating data
SQL database for persistent storage
Docker for containerized development and deployment
Local server setup for development and testing
Strawberry GraphQL library with FastAPI integration
Prerequisites

Ensure you have the following installed on your local machine:

Docker
Python (version 3.8+)
pip (Python package installer)
Installation

Clone the repository:

bash
Copy code
git clone https://github.com/yourusername/your-repo-name.git
cd your-repo-name
Install dependencies:

Create a virtual environment and install the required packages:

bash
Copy code
python -m venv venv
source venv/bin/activate  # On Windows use `venv\Scripts\activate`
pip install -r requirements.txt
Set up environment variables:

Create a .env file in the root directory and add your configuration. Example:

env
Copy code
DATABASE_URL=postgres://user:password@localhost:5432/mydatabase
Running the Project

Start Docker containers:

Ensure Docker is running on your machine. Then, start the containers:

bash
Copy code
docker-compose up -d
Run database migrations:

Apply any necessary migrations to set up the database schema. This step will vary depending on your migration tool, for example:

bash
Copy code
alembic upgrade head
Start the FastAPI server:

Launch the server on your local machine:

bash
Copy code
uvicorn app.main:app --reload
The server will be running at http://localhost:8000/graphql.

Usage

Access the GraphQL playground by navigating to http://localhost:8000/graphql in your browser.
Use the playground to execute GraphQL queries and mutations.
Example Query
graphql
Copy code
query {
  users {
    id
    name
    email
  }
}
Example Mutation
graphql
Copy code
mutation {
  createUser(input: { name: "John Doe", email: "john.doe@example.com" }) {
    id
    name
    email
  }
}
Project Structure

bash
Copy code
your-repo-name/
├── app/
│   ├── __init__.py
│   ├── main.py          # Entry point of the application
│   ├── schema/
│   │   ├── types.py     # GraphQL type definitions
│   │   └── resolvers.py # GraphQL resolvers
│   ├── db/
│   │   ├── models.py    # Database models
│   │   └── migrations/  # Database migrations
├── .env                 # Environment variables
├── docker-compose.yml   # Docker Compose configuration
├── Dockerfile           # Dockerfile for building the API service
├── requirements.txt     # Project dependencies
└── README.md            # Project documentation
Contributing

Contributions are welcome! Please fork the repository and create a pull request with your changes.

Fork the repository.
Create your feature branch (git checkout -b feature/awesome-feature).
Commit your changes (git commit -m 'Add awesome feature').
Push to the branch (git push origin feature/awesome-feature).
Open a pull request.
License

This project is licensed under the MIT License. See the LICENSE file for details.

