<p align="center">
  <a href="http://nestjs.com/" target="blank"><img src="https://nestjs.com/img/logo-small.svg" width="120" alt="Nest Logo" /></a>
</p>

<p align="center">
  <img src="./notification-system.png" alt="System Architecture" />
</p>

<h1 align="center">IAM Service</h1>

<p align="center">
  <a href="https://www.npmjs.com/package/@nestjs/core" target="_blank"><img src="https://img.shields.io/npm/v/@nestjs/core.svg" alt="NPM Version" /></a>
  <a href="https://www.npmjs.com/package/@nestjs/core" target="_blank"><img src="https://img.shields.io/npm/l/@nestjs/core.svg" alt="Package License" /></a>
  <a href="https://www.npmjs.com/package/@nestjs/core" target="_blank"><img src="https://img.shields.io/npm/dm/@nestjs/common.svg" alt="NPM Downloads" /></a>
  <a href="https://circleci.com/gh/your-org/iam-service" target="_blank"><img src="https://img.shields.io/circleci/build/github/your-org/iam-service" alt="Build Status" /></a>
  <a href="https://codecov.io/gh/your-org/iam-service" target="_blank"><img src="https://codecov.io/gh/your-org/iam-service/branch/main/graph/badge.svg" alt="Code Coverage" /></a>
</p>

## Description

Identity and Access Management (IAM) Service built with [NestJS](https://nestjs.com/). This service is responsible for user authentication, authorization, and session management across the system.

### Key Features

- 🔐 JWT-based authentication
- 🔑 Role-based access control (RBAC)
- 👥 User management
- 🔄 Session management
- 🔒 Secure password hashing with bcrypt
- 📱 Support for multiple authentication strategies
- 🛡️ Rate limiting and security best practices

## 🚀 Getting Started

### Prerequisites

- Node.js (v16 or later)
- npm or yarn
- Redis (for session management)
- PostgreSQL (for data persistence)

### Installation

1. Clone the repository
2. Install dependencies:

```bash
npm install
```

3. Copy the environment file and update the values:

```bash
cp .env.example .env
```

4. Start the development server:

```bash
# development
npm run start

# watch mode
npm run start:dev

# production mode
npm run start:prod
```

## API Documentation

Once the application is running, you can access the API documentation at:

- Swagger UI: `http://localhost:3000/api`
- OpenAPI JSON: `http://localhost:3000/api-json`

## Environment Variables

Create a `.env` file in the root directory with the following variables:

```env
# App
NODE_ENV=development
PORT=3000

# Database
DATABASE_URL=postgresql://user:password@localhost:5432/iam

# JWT
JWT_SECRET=your_jwt_secret
JWT_EXPIRES_IN=1d

# Redis
REDIS_HOST=localhost
REDIS_PORT=6379

# Session
SESSION_SECRET=your_session_secret
SESSION_EXPIRATION=86400
```

## Testing

```bash
# unit tests
npm run test

# e2e tests
npm run test:e2e

# test coverage
npm run test:cov

# test watch mode
npm run test:watch
```

## Deployment

### Docker

Build and run using Docker:

```bash
docker-compose up --build
```

### Production

For production deployments, make sure to:

1. Set `NODE_ENV=production`
2. Configure proper SSL/TLS
3. Set up monitoring and logging
4. Configure proper security headers
5. Set up rate limiting

## Architecture

The IAM service follows a clean architecture pattern with the following layers:

- **Controllers**: Handle HTTP requests and responses
- **Services**: Contain business logic
- **Repositories**: Handle data access
- **Entities**: Define data models
- **DTOs**: Data transfer objects for input/output validation
- **Guards**: Protect routes based on authentication/authorization
- **Interceptors**: Handle cross-cutting concerns like logging, error handling

## API Endpoints

### Authentication

- `POST /auth/register` - Register a new user
- `POST /auth/login` - Authenticate user and get JWT token
- `POST /auth/refresh` - Refresh access token
- `POST /auth/logout` - Invalidate user session

### Users

- `GET /users` - Get all users (admin only)
- `GET /users/:id` - Get user by ID
- `PUT /users/:id` - Update user
- `DELETE /users/:id` - Delete user

### Roles & Permissions

- `GET /roles` - Get all roles
- `POST /roles` - Create a new role
- `PUT /roles/:id` - Update role permissions
- `DELETE /roles/:id` - Delete role

## Security

- JWT authentication with refresh tokens
- Role-based access control (RBAC)
- Rate limiting
- Request validation
- Helmet for security headers
- CORS protection
- CSRF protection
- Input sanitization

## Monitoring

- Health checks at `/health`
- Prometheus metrics at `/metrics`
- Structured logging with correlation IDs
- Distributed tracing

## Contributing

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## License

This project is [MIT licensed](LICENSE).

## Support

For support, please open an issue in the repository or contact the maintainers.

## Acknowledgments

- [NestJS](https://nestjs.com/) - A progressive Node.js framework
- [TypeORM](https://typeorm.io/) - ORM for TypeScript and JavaScript
- [Passport](http://www.passportjs.org/) - Authentication middleware for Node.js
