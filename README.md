# Social Media Application Backend

This repository is a root directory social media application. It has two hooks to submodule repositories - backend built with GoLang and frontend built with Next.js.


## Prerequisites

- Docker and Docker Compose
- Git
- Go 1.23 or higher

## Getting Started

### 1. Clone the Repository

```bash
git clone --recursive https://git@github.com:mikorozek/socialmedia-application-backend.git
cd socialmedia-application-backend
```

### 2. Environment Configuration

Create a `.env` file in the root directory with the following variables:

```env_example
POSTGRES_DB=<db_name>
POSTGRES_USER=<user>
POSTGRES_PASSWORD=<password>
POSTGRES_PORT=<db_port>
BACKEND_PORT=<backend_port>
BACKEND_HOST=backend
FRONTEND_PORT=<frontend_port>
FRONTEND_HOST=frontend
NODE_ENV=production
```

Replace .env variables with your desired values. BACKEND_HOST and FRONTEND_HOST are backend and frontend service names in docker-compose.yml file.

Create a second `.env` file in the socialmedia-application-frontend directory with the following variables:
```env_example
NEXTAUTH_SECRET=<secret>
NEXTAUTH_URL=http://localhost:<frontend_port>/
NEXT_PUBLIC_BACKEND_HOST=backend
NEXT_PUBLIC_BACKEND_PORT=<backend_port>
```

Replace .env variables with your desired values. NEXT_PUBLIC_BACKEND_HOST is a backend service name in docker-compose.yml file.

### 3. Start the Application

Run the following command to start all services:

```bash
docker compose up --build
```

This will:
- Start a PostgreSQL database container
- Build and start the backend service
- Set up all necessary networking between services

### 4. Verify Installation

Check if the services are running:

```bash
docker compose ps
```

Test the API endpoint:

```bash
curl http://localhost:8080/api/health
```

## Backend Project Structure

```
.
├── cmd/                    # Application entrypoints
├── internal/              # Private application code
│   ├── Auth/             # Authentication module
│   └── shared/           # Shared code between modules
└── docker/               # Docker-related files
```

### CI/CD

The project includes:
- Jenkins CI pipeline for automated testing
- Jenkins CD pipeline for deployment
- Infrastructure as Code using Terraform

## License

This project is licensed under the MIT License - see the LICENSE file for details.
