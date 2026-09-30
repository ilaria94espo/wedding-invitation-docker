# Wedding Invitation Docker

A simple web application for a wedding invitation, containerized with Docker and orchestrated with Docker Compose.

The project consists of a frontend, a Node.js backend and a PostgreSQL database.

## Architecture

The application is composed of three Docker containers:

- **Frontend**: Nginx serving the static HTML, CSS and JavaScript files
- **Backend**: Node.js with Express
- **Database**: PostgreSQL

The backend communicates with the PostgreSQL database through the Docker Compose network.

```text
Browser
   |
   v
Frontend (Nginx)
   |
   v
Backend (Node.js / Express)
   |
   v
PostgreSQL


Technologies
HTML
CSS
JavaScript
Nginx
Node.js
Express
PostgreSQL
Docker
Docker Compose
Docker Setup

The project uses Docker Compose to start all application services.

Services
Service	Technology	Port
frontend	Nginx	8081
backend	Node.js / Express	3000
database	PostgreSQL	5432

The PostgreSQL database uses a named Docker volume to persist its data:

postgres_data

The database data therefore remains available when the containers are stopped and recreated.

Environment Variables

Database credentials are stored in a .env file and are not committed to the repository.

Example configuration:

POSTGRES_DB=wedding
POSTGRES_USER=wedding_user
POSTGRES_PASSWORD=change_me

An example file is provided as:

.env.example

Before starting the application, create a .env file based on .env.example.

Requirements
Docker Desktop
Docker Compose
Start the Application

Clone the repository and enter the project directory:

git clone https://github.com/ilaria94espo/wedding-invitation-docker.git
cd wedding-invitation-docker

Create the .env file:

POSTGRES_DB=wedding
POSTGRES_USER=wedding_user
POSTGRES_PASSWORD=wedding_password

Start all containers:

docker compose up --build -d

Check the running containers:

docker compose ps
Access the Application

Frontend:

http://localhost:8081

Backend health check:

http://localhost:3000/api/health

Database connection test:

http://localhost:3000/api/db-test

The database test should return a JSON response confirming that the backend is connected to PostgreSQL.

Stop the Application

To stop the containers:

docker compose down

The named PostgreSQL volume is not deleted by this command.

To completely remove the containers and the database volume:

docker compose down -v

Warning: removing the volume also removes the persisted PostgreSQL data.

Project Structure
wedding-invitation-docker/
│
├── backend/
│   ├── Dockerfile
│   ├── package.json
│   ├── package-lock.json
│   └── server.js
│
├── css/
├── js/
├── assets/
│
├── Dockerfile
├── docker-compose.yml
├── .env.example
├── .gitignore
└── README.md
Docker Requirements Demonstrated

This project demonstrates:

Containerization using Dockerfiles
Docker Compose orchestration
Multiple containers
Communication between containers
Node.js backend
PostgreSQL database
Persistent data using a named volume
Environment variables for database credentials
Separation of application services