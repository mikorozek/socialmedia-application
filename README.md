# Social Media Application Backend

This repository contains the backend service for a social media application, built with Go and PostgreSQL.

## Prerequisites

- Docker and Docker Compose
- Git
- Go 1.23 or higher

## Getting Started

### 1. Clone the Repository

```bash
git clone --recursive git@github.com:mikorozek/socialmedia-application-backend.git
cd socialmedia-application-backend
```

### 2. Environment Configuration

Create a `.env` file in the root directory with the following variables:

```env
POSTGRES_DB=socialmedia_db
POSTGRES_USER=your_username
POSTGRES_PASSWORD=your_password
POSTGRES_PORT=5432
BACKEND_PORT=8080
FRONTEND_HOST=localhost
FRONTEND_PORT=3000
```

Replace `your_username` and `your_password` with your desired database credentials.

### 3. Start the Application

Run the following command to start all services:

```bash
docker compose up -d
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

## Project Structure

```
.
├── cmd/                    # Application entrypoints
├── internal/              # Private application code
│   ├── Auth/             # Authentication module
│   └── shared/           # Shared code between modules
├── infrastructure/        # Infrastructure configuration
└── docker/               # Docker-related files
```

## Development

### Running Tests

```bash
go test ./... -v
```

### CI/CD

The project includes:
- Jenkins CI pipeline for automated testing
- Jenkins CD pipeline for deployment
- Infrastructure as Code using Terraform

## API Endpoints

### Authentication

- `POST /api/verify/register` - Register a new user
- `POST /api/verify/login` - Login user

## Troubleshooting

1. If containers don't start:
   ```bash
   docker compose logs
   ```

2. If database connection fails:
   - Verify your `.env` configuration
   - Check if PostgreSQL container is running
   - Ensure database port is not already in use

## Contributing

1. Fork the repository
2. Create your feature branch
3. Commit your changes
4. Push to the branch
5. Create a Pull Request

## License

This project is licensed under the MIT License - see the LICENSE file for details.
