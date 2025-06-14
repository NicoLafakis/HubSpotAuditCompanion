# The Playground

> **HubSpot Sandbox Data Generator**  
> Transform empty CRM environments into realistic working examples with intelligent synthetic data generation.

![The Playground Dashboard](https://via.placeholder.com/800x400/0F172A/F8FAFC?text=The+Playground+Dashboard)

## Overview

The Playground is a sophisticated web application that connects to HubSpot CRM environments and populates them with lifelike synthetic data. Featuring a futuristic command center interface with premium open spacing design, it generates realistic contacts, companies, deals, and activities that mimic authentic customer interactions over time.

### Key Features

- **🎨 Premium Interface**: Dark-themed UI with hot pink, electric blue, and red-orange neon accents
- **🔐 Secure Integration**: OAuth-based HubSpot API connection with encrypted credential storage
- **🎯 Intelligent Data Generation**: Realistic synthetic data with natural relationship patterns
- **📊 Real-time Monitoring**: Live progress tracking with terminal-style activity logs
- **⚙️ Advanced Configuration**: Granular control over data types, quantities, and timeframes
- **💾 Template System**: Save and reuse configuration templates for different scenarios
- **🚀 Performance Optimized**: Respects HubSpot API rate limits with intelligent batching

## Technology Stack

### Frontend
- **React 18** with TypeScript for type safety
- **Redux Toolkit** for state management
- **Tailwind CSS** with custom theming
- **Framer Motion** for animations
- **D3.js** for data visualizations
- **Vite** for build tooling

### Backend
- **Node.js** with Express framework
- **MongoDB** for data persistence
- **Socket.IO** for real-time updates
- **JWT** for authentication
- **HubSpot API** integration

### Development Tools
- **ESLint** + **Prettier** for code quality
- **Jest** + **React Testing Library** for testing
- **Docker** for containerization
- **GitHub Actions** for CI/CD

## Quick Start

### Prerequisites

- Node.js 18+ and npm
- MongoDB instance
- HubSpot developer account with API access

### Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/your-username/the-playground.git
   cd the-playground
   ```

2. **Install dependencies**
   ```bash
   # Install backend dependencies
   npm install

   # Install frontend dependencies
   cd client
   npm install
   cd ..
   ```

3. **Environment Configuration**
   ```bash
   # Copy environment template
   cp .env.example .env
   
   # Edit with your configuration
   nano .env
   ```

4. **Required Environment Variables**
   ```env
   # Database
   MONGODB_URI=mongodb://localhost:27017/playground
   
   # Authentication
   JWT_SECRET=your-super-secret-jwt-key
   ENCRYPTION_KEY=your-32-character-encryption-key
   
   # HubSpot Integration
   HUBSPOT_CLIENT_ID=your-hubspot-client-id
   HUBSPOT_CLIENT_SECRET=your-hubspot-client-secret
   HUBSPOT_REDIRECT_URI=http://localhost:3000/auth/callback
   
   # Application
   PORT=3001
   NODE_ENV=development
   ```

5. **Start Development Servers**
   ```bash
   # Start backend (Terminal 1)
   npm run dev

   # Start frontend (Terminal 2)
   cd client
   npm run dev
   ```

6. **Access the Application**
   - Frontend: http://localhost:3000
   - Backend API: http://localhost:3001

## Usage Guide

### Initial Setup

1. **Create Account**: Register with your email and secure password
2. **Connect HubSpot**: Authorize access to your HubSpot account via OAuth
3. **Verify Connection**: Confirm API connectivity and permissions

### Basic Data Generation

1. **Quick Start**: Use default configuration for immediate data generation
2. **Configure Parameters**: Adjust contact counts, company types, and deal stages
3. **Set Timeline**: Define the timeframe for historical activity generation
4. **Launch Simulation**: Monitor progress through the real-time dashboard

### Advanced Configuration

#### Contact Generation
```yaml
Contact Types:
  - Leads: 40%
  - Customers: 35%
  - Partners: 15%
  - Prospects: 10%

Demographics:
  - Geographic distribution
  - Industry alignment
  - Company size correlation
```

#### Relationship Mapping
```yaml
Relationships:
  - Contact → Company associations
  - Deal → Contact ownership
  - Activity → Contact interactions
  - Custom property correlations
```

#### Activity Patterns
```yaml
Activity Types:
  - Email communications (60%)
  - Meeting scheduling (25%)
  - Call logging (10%)
  - Task completion (5%)

Timing Distribution:
  - Business hours weighting
  - Seasonal patterns
  - Industry-specific cycles
```

### Template Management

1. **Save Configuration**: Store current settings as named templates
2. **Load Templates**: Quick-start with pre-configured scenarios
3. **Share Templates**: Export/import configurations between teams
4. **Template Categories**: Organize by industry, company size, or use case

## API Documentation

### Authentication Endpoints

```http
POST /auth/register
POST /auth/login
POST /auth/refresh
DELETE /auth/logout
```

### HubSpot Integration

```http
GET /api/hubspot/connect
POST /api/hubspot/callback
GET /api/hubspot/status
DELETE /api/hubspot/disconnect
```

### Simulation Management

```http
POST /api/simulation/start
PUT /api/simulation/pause
PUT /api/simulation/resume
DELETE /api/simulation/stop
GET /api/simulation/status
GET /api/simulation/logs
```

### Configuration Templates

```http
GET /api/templates
POST /api/templates
PUT /api/templates/:id
DELETE /api/templates/:id
```

## Development

### Project Structure

```
the-playground/
├── client/                 # React frontend
│   ├── src/
│   │   ├── components/     # Reusable UI components
│   │   ├── pages/          # Page components
│   │   ├── store/          # Redux state management
│   │   ├── hooks/          # Custom React hooks
│   │   ├── utils/          # Utility functions
│   │   └── styles/         # Global styles and themes
│   ├── public/
│   └── package.json
├── server/                 # Node.js backend
│   ├── src/
│   │   ├── controllers/    # Route handlers
│   │   ├── middleware/     # Express middleware
│   │   ├── models/         # Database models
│   │   ├── services/       # Business logic
│   │   ├── utils/          # Utility functions
│   │   └── routes/         # API routes
│   └── package.json
├── docs/                   # Documentation
├── docker-compose.yml      # Docker configuration
└── README.md
```

### Code Style Guidelines

- **TypeScript**: Strict type checking enabled
- **ESLint**: Airbnb configuration with custom rules
- **Prettier**: Consistent code formatting
- **Conventional Commits**: Structured commit messages

### Testing Strategy

```bash
# Run all tests
npm run test

# Frontend tests
cd client && npm run test

# Backend tests
npm run test:server

# E2E tests
npm run test:e2e
```

### Building for Production

```bash
# Build frontend
cd client && npm run build

# Build backend
npm run build

# Build Docker images
docker-compose build
```

## Deployment

### Using Docker

```bash
# Production deployment
docker-compose -f docker-compose.prod.yml up -d

# Check status
docker-compose ps

# View logs
docker-compose logs -f
```

### Environment-Specific Configuration

#### Development
- Hot reloading enabled
- Detailed error messages
- Development HubSpot sandbox

#### Staging
- Production build with source maps
- Staging HubSpot environment
- Performance monitoring

#### Production
- Optimized builds
- Error tracking with Sentry
- Production HubSpot integration
- Automated backups

## Security Considerations

### Data Protection
- **Encryption**: All HubSpot API keys encrypted at rest
- **HTTPS**: Enforced SSL/TLS for all communications
- **CSRF Protection**: Token-based request validation
- **Rate Limiting**: API endpoint protection
- **Input Validation**: Comprehensive data sanitization

### Authentication & Authorization
- **JWT Tokens**: Secure session management
- **OAuth 2.0**: HubSpot API authorization
- **Role-Based Access**: User permission levels
- **Session Management**: Automatic token refresh

## Performance Optimization

### Frontend
- **Code Splitting**: Dynamic imports for reduced bundle size
- **Lazy Loading**: Component-level loading optimization
- **Memoization**: React.memo and useMemo implementations
- **Virtual Scrolling**: Efficient handling of large data sets

### Backend
- **Connection Pooling**: Optimized database connections
- **Caching**: Redis-based response caching
- **Rate Limiting**: HubSpot API quota management
- **Background Jobs**: Asynchronous data processing

## Contributing

We welcome contributions! Please read our [Contributing Guide](CONTRIBUTING.md) for details on:

- Code of conduct
- Development process
- Pull request guidelines
- Issue reporting

### Development Setup

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit changes (`git commit -m 'Add amazing feature'`)
4. Push to branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## Support

### Documentation
- [User Guide](docs/user-guide.md)
- [API Reference](docs/api-reference.md)
- [Deployment Guide](docs/deployment.md)
- [Troubleshooting](docs/troubleshooting.md)

### Community
- [GitHub Discussions](https://github.com/your-username/the-playground/discussions)
- [Discord Server](https://discord.gg/playground)
- [Stack Overflow](https://stackoverflow.com/questions/tagged/the-playground)

### Commercial Support
For enterprise support, custom integrations, or consulting services, contact [support@theplayground.dev](mailto:support@theplayground.dev).

## Roadmap

### v2.0 (Q2 2025)
- [ ] Multi-CRM support (Salesforce, Pipedrive)
- [ ] Advanced AI-powered data generation
- [ ] Custom workflow automation
- [ ] Enterprise SSO integration

### v2.1 (Q3 2025)
- [ ] Real-time collaboration features
- [ ] Advanced analytics dashboard
- [ ] Custom data source integration
- [ ] Mobile application

### v3.0 (Q4 2025)
- [ ] Machine learning data patterns
- [ ] API marketplace integration
- [ ] White-label solutions
- [ ] Advanced compliance features

## License

This project is licensed under the Apache License 2.0 - see the [LICENSE](LICENSE) file for details.

```
Copyright 2025 The Playground Project

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

    http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
```

## Acknowledgments

- HubSpot for their comprehensive API
- The React and Node.js communities
- Contributors and early adopters
- Open source libraries that made this possible

---

**Built with ❤️ by the Playground Team**

For questions, suggestions, or support, reach out at [hello@theplayground.dev](mailto:hello@theplayground.dev)
