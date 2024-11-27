# Next.js 15 PocketBase SaaS Template

## Table of Contents

- [Introduction](#introduction)
- [Features](#features)
- [Technologies Used](#technologies-used)
- [Prerequisites](#prerequisites)
- [Installation](#installation)
- [Running the Application](#running-the-application)
- [Environment Variables](#environment-variables)
- [Docker Setup](#docker-setup)
- [Development](#development)
- [Health Checks](#health-checks)
- [Notes](#notes)
- [Contributing](#contributing)
- [License](#license)
- [Accessing the Next.js Application](#accessing-the-next-js-application)
- [Accessing PocketBase](#accessing-pocketbase)
- [ShadCN Configuration](#shadcn-configuration)
- [Extended Documentation](#extended-documentation)

## Introduction

Welcome to the **Next.js 15 PocketBase SaaS Template**! This project serves as a robust starting point for building scalable SaaS applications. It leverages the power of Next.js for the frontend and PocketBase for the backend, all containerized with Docker for seamless deployment.

**Please note:** This project is **not** Vercel-friendly. It is specifically designed to be **self-hosted** using Docker to ensure full control over your deployment environment.

## Features

- **Next.js 15:** Server-side rendering and static site generation for optimal performance.
- **PocketBase:** Lightweight and scalable backend solution.
- **Dockerized Setup:** Simplifies deployment and ensures consistency across environments.
- **Tailwind CSS:** Utility-first CSS framework for rapid UI development.
- **TypeScript Support:** Enhances code quality and maintainability.
- **Automated Health Checks:** Ensures application and services are running smoothly.
- **Extensible Configuration:** Easily customizable to fit your project's needs.

## Technologies Used

- [Next.js](https://nextjs.org/) - React framework for production.
- [PocketBase](https://pocketbase.io/) - Open-source backend.
- [Docker](https://www.docker.com/) & [Docker Compose](https://docs.docker.com/compose/) - Containerization tools.
- [Tailwind CSS](https://tailwindcss.com/) - Utility-first CSS framework.
- [TypeScript](https://www.typescriptlang.org/) - Typed JavaScript.
- [Jest](https://jestjs.io/) & [Cypress](https://www.cypress.io/) - Testing frameworks.

## Prerequisites

Before setting up the project, ensure you have the following installed on your machine:

- [Docker](https://www.docker.com/get-started)
- [Docker Compose](https://docs.docker.com/compose/install/)
- [Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)
- [PocketBase](https://pocketbase.io)
- [Next.js](https://nextjs.org)

## Installation

1. **Clone the Repository**

   ```bash
   git clone https://github.com/tao101/nextjs-pocketbase-saas-template.git
   cd nextjs-pocketbase-saas-template
   ```

2. **Configure Environment Variables**

   - Copy the example environment file to both development and production environments:

     ```bash
     cp .env.example .env.development
     cp .env.example .env.production
     ```

   - Open the `.env.development` and `.env.production` files and fill in the required environment variables:

     ```env
     NEXT_PUBLIC_POCKETBASE_URL=http://localhost:8090
     PB_TYPEGEN_EMAIL=your-email@example.com
     PB_TYPEGEN_PASSWORD=your-password
     ```

## Running the Application

### Using Docker Compose

This project is optimized to run using Docker Compose, which orchestrates both the Next.js frontend and PocketBase backend.

1. **Build and Start the Containers**

   - For **Development**:

     ```bash
     npm run docker
     ```

   - For **Production**:

     ```bash
     docker compose -f docker-compose.yml up
     ```

   These commands build the Docker images and start the services as defined in the `docker-compose.yml` or `docker-compose.dev.yml` file.

2. **Access the Application**

   - Open your browser and navigate to [http://localhost:3000](http://localhost:3000) to view the application.
   - Access PocketBase admin panel at [http://localhost:8090/\_/](http://localhost:8090/_) for backend management.

### Development Mode

For development purposes, you can use `docker-compose.dev.yml` to run the application with hot-reloading.

```bash
npm run docker
```

## PocketBase typegen

Ensure that the `.env.development` and `.env.production` files contain all necessary environment variables. Here's a brief overview:

- `NEXT_PUBLIC_POCKETBASE_URL`: URL where PocketBase is running.
- `PB_TYPEGEN_EMAIL`: Email for PocketBase type generation.
- `PB_TYPEGEN_PASSWORD`: Password for PocketBase type generation.

we are using [pocketbase-typegen](https://github.com/pocketbase/pocketbase-typegen) to generate the types for PocketBase.

// Start Generation Here

### Running the Typegen Script

To generate the PocketBase types, you can run the following commands:

- **Locally**:

  Ensure that the `POCKETBASE_URL` environment variable is set before running the typegen script.

  ```bash
  npm run typegen
  ```

- **Using Docker**:

  ```bash
  npm run docker:typegen
  ```

  the types will be generated in the `pocketbase-types.ts` file in the root of the project.

## Docker Setup

The project utilizes Docker for containerization, ensuring a consistent environment across different machines.

### Services

- **nextjs**: The Next.js frontend application.
- **pocketbase**: The PocketBase backend service.

### Volumes

- `pocketbase_data`: Persists PocketBase data.
- `pocketbase_public`: Serves public files for PocketBase.
- `node_modules` & `next-cache`: Manage dependencies and cache for faster builds.

### Health Checks

The `docker-compose.yml` includes health checks to ensure all services are running correctly.

## Health Checks

Health checks are implemented to monitor the status of both Next.js and PocketBase services.

- **Next.js Health Check**: `http://localhost:3000/api/health`
- **PocketBase Health Check**: `http://localhost:8090/api/health`

These endpoints help Docker Compose manage service health and restarts automatically if needed.

## Notes

- **Vercel Incompatibility**: This project is not compatible with Vercel deployments due to its reliance on the self-hosted PocketBase backend. For seamless operation, it's recommended to host the application using Docker as outlined above.
- **Customization**: Feel free to modify the Tailwind CSS configurations, Docker settings, and other configurations to suit your project's requirements.

## Contributing

Contributions are welcome! Please follow these steps:

1. **Fork the Repository**

2. **Create a Feature Branch**

   ```bash
   git checkout -b feature/YourFeature
   ```

3. **Commit Your Changes**

   ```bash
   git commit -m "Add your message"
   ```

4. **Push to the Branch**

   ```bash
   git push origin feature/YourFeature
   ```

5. **Open a Pull Request**

## License

This project is licensed under the [MIT License](LICENSE).

## Accessing the Next.js Application

After running the application using Docker Compose, you can access the Next.js frontend by navigating to [http://localhost:3000](http://localhost:3000) in your web browser.

## Accessing PocketBase

PocketBase serves as the backend for this application. To access the PocketBase admin panel:

1. Ensure the PocketBase service is running via Docker Compose.

2. Open your browser and go to [http://localhost:8090/\_/](http://localhost:8090/_/).

3. the first time you run the application, you will need to create a new user account to login to the PocketBase admin panel. you will find the url to access the admin panel in the terminal.

## ShadCN Configuration

This project is configured to use [ShadCN](https://ui.shadcn.com/) for building accessible and customizable UI components.

**Benefits of using ShadCN:**

- **Accessibility:** Compliant with WCAG standards.
- **Customization:** Easy to extend and customize components.
- **Consistency:** Maintains a consistent design system across the application.

**Configuration Details:**

The ShadCN configuration is located in the `components.json` file, which defines aliases, Tailwind CSS integration, and icon library settings.

For more information on customizing ShadCN components, refer to the [official documentation](https://ui.shadcn.com/docs).

## Extended Documentation

For more in-depth information about the project's architecture, component structure, and customization options, refer to the [Documentation](./docs/README.md).

You can also explore the source code to understand how various features are implemented and interact with each other.
