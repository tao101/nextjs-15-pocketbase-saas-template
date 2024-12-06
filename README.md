Based on the provided code and README, here's an improved documentation:

# Next.js 15 PocketBase SaaS Template

## Table of Contents

[Preserving existing table of contents structure]

## Introduction

Welcome to the **Next.js 15 PocketBase SaaS Template**! This project provides a robust foundation for building self-hosted SaaS applications using Next.js 15 and PocketBase. The template is fully containerized with Docker and includes modern development tools and practices.

**Important:** This template is designed specifically for self-hosted deployments using Docker and is not compatible with Vercel hosting.

## Features

- **Next.js 15** with App Router and Server Components
- **PocketBase Backend** with TypeScript type generation
- **Docker & Docker Compose** configuration for both development and production
- **ShadCN UI Components** for accessible and customizable UI
- **Tailwind CSS** integration
- **TypeScript** throughout the codebase
- **Health Check Endpoints** for monitoring
- **Development Tools:**
  - ESLint configuration
  - PostCSS setup
  - Modern asset handling (SVG support)

## Prerequisites

- Docker & Docker Compose
- Node.js (for local development)
- Git

## Quick Start

1. **Clone and Setup:**
   ```bash
   git clone https://github.com/tao101/nextjs-pocketbase-saas-template.git
   cd nextjs-pocketbase-saas-template
   cp .env.example .env.development
   cp .env.example .env.production
   ```

2. **Configure Environment:**
   ```env
   NEXT_PUBLIC_POCKETBASE_URL=http://localhost:8090
   PB_TYPEGEN_EMAIL=your-email@example.com
   PB_TYPEGEN_PASSWORD=your-password
   ```

3. **Start Development Environment:**
   ```bash
   npm run docker
   ```

## Development Tools

### PocketBase Type Generation

The template uses `pocketbase-typegen` to generate TypeScript types from your PocketBase schema:

```bash
# Local generation
npm run typegen

# Docker-based generation
npm run docker:typegen
```

### Health Checks

Built-in health check endpoints:
- Frontend: `http://localhost:3000/api/health`
- Backend: `http://localhost:8090/api/health`

### Project Structure

```
├── app/                 # Next.js app directory
│   ├── api/            # API routes
│   ├── globals.css     # Global styles
│   └── layout.tsx      # Root layout
├── lib/                # Utility functions
├── public/             # Static assets
└── docker/             # Docker configuration
```

## Docker Configuration

The project includes two Docker Compose configurations:

- `docker-compose.yml`: Production setup
- `docker-compose.dev.yml`: Development environment with hot-reload

### Volumes:
- `pocketbase_data`: Database persistence
- `pocketbase_public`: Public file storage
- `node_modules`: Dependencies
- `next-cache`: Build cache

## UI Components

The template uses ShadCN UI components, configured in `components.json`. These components are:
- Accessible (WCAG compliant)
- Customizable via Tailwind CSS
- Type-safe with TypeScript

## Contributing

Contributions are welcome! Please:
1. Fork the repository
2. Create a feature branch
3. Submit a Pull Request

## License

MIT License

---

**Note:** This template is actively maintained and follows modern development practices. For detailed usage and customization instructions, refer to the inline documentation in the codebase.
