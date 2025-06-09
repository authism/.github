# Authism Organization

Welcome to the Authism organization! This document outlines our global development standards, architectural patterns, and company-wide practices that apply across all projects.

---

## 🏗️ Global Architecture Standards

### Monorepo Strategy with Turborepo
All Authism services are developed within **monorepos**, managed by **Turborepo**. This approach provides:
- **Atomic Commits:** Changes across multiple services (e.g., an API and its consumer) are made in a single, traceable commit.
- **Simplified Dependency Management:** Shared libraries and types are easily managed across the entire application.
- **Optimized CI/CD:** Turborepo intelligently determines which services are affected by a change, ensuring that only the necessary code is built, tested, and deployed.

### Technology Philosophy
As a green firm, Authism prioritizes modern, performant, and safe technologies:

#### Backend Standards
- **Primary**: Rust for all backend services (memory safety, performance, modern practices)
- **Secondary**: TypeScript with Bun for rapid development or team expertise requirements
- **Additional Options**: Python/FastAPI, Go/Gin, Java/Spring (situational use)

#### Frontend Standards
- **Framework**: Next.js with React (Multi-platform support)
- **Testing**: Jest for comprehensive test coverage
- **Deployment**: Containerized with Docker, served via Nginx
- **Build Tool**: Next.js's integrated build system, orchestrated by Turborepo

#### Data & Communication Standards
- **Database**: PostgreSQL (primary data store)
- **Caching**: Redis for session and query caching
- **Message Queue**: RabbitMQ for asynchronous service communication
- **Service Communication**: gRPC for internal APIs
- **External APIs**: RESTful endpoints for client integration

---

## 🚀 Infrastructure Standards

### Self-Hosted Philosophy
Authism maintains full control over critical infrastructure with minimal external dependencies:

**Self-Hosted Components:**
- Kubernetes cluster for container orchestration
- PostgreSQL and Redis databases
- All microservices and APIs
- CI/CD pipeline infrastructure

**Approved External Services:**
- **Cloudflare**: Edge delivery, DNS, and security
- **Cloudflare R2**: Object storage for files and media

### Deployment Standards
- **Containerization**: Docker for all services
- **Orchestration**: Kubernetes with custom manifests
- **Build System**: **Turborepo** for high-performance, incremental builds and dependency management
- **CI/CD**: GitHub Actions with automated testing. Workflows are optimized by Turborepo to only run jobs on affected services
- **Monitoring**: Prometheus/Grafana stack (standard across all projects)
- **Networking**: Nginx ingress with Cloudflare Tunnels

---

## 🛠️ Development Standards

### Standardized Commit Messages
To maintain a clear, understandable, and automated Git history, we adhere to the [Conventional Commits](https://www.conventionalcommits.org/en/v1.0.0/) specification. This structured format enables automatic versioning and changelog generation. **All commits must follow this standard.** Commits that do not follow this format will be rejected and must be reworded.

**Commit Message Format:**

- **Structure:** `type(scope): subject`
- **Common Types:**
  - `feat`: A new feature for the end-user
  - `fix`: A bug fix for the end-user
  - `docs`: Documentation changes only
  - `style`: Code style changes (formatting, etc; no production code change)
  - `refactor`: Refactoring production code, e.g. renaming a variable
  - `test`: Adding/updating tests; no production code change
  - `chore`: Updating dependencies, build configs, etc; no production code change
- **Breaking Changes:** Use `!` after the type for breaking changes (e.g., `refactor(auth)!: ...`)

**Examples:**
```
feat: allow users to upload profile pictures
fix(api): correct pagination error on jobs endpoint
docs: update authentication service README
refactor!: rename primary key from id to user_id in users table
```

### Development Workflow
- **Methodology**: Agile with Scrum in a monorepo structure
- **Sprint Planning**: Sprint-based development cycles with cross-functional collaboration
- **Code Review**: All changes require pull requests with CODEOWNERS-based automatic reviewer assignment
- **Testing**: Comprehensive unit and integration testing enforced across all services

### Quality Assurance Standards
- **Unit Testing**: Jest for frontend, language-specific frameworks for backend
- **Integration Testing**: End-to-end API testing orchestrated by Turborepo
- **Code Quality**: Automated linting and formatting enforced across the entire monorepo
- **Security**: Regular dependency audits and vulnerability scanning

---

## 🔒 Security & Compliance Standards

### Authentication Standards
- **Protocol**: OAuth 2.0 with JWT tokens
- **Password Security**: Argon2 hashing algorithm (minimum standard)
- **Data Protection**: Encrypted data transmission and storage
- **Infrastructure Security**: Regular security audits and updates
- **Privacy**: GDPR-compliant data handling practices

### Security Requirements
- All services must implement proper authentication and authorization
- Sensitive data must be encrypted at rest and in transit
- Regular security audits and dependency vulnerability scans
- Incident response procedures must be documented and tested

---

## 📊 Monitoring & Observability Standards

**Required Implementation for All Projects:**
- Application performance monitoring
- Infrastructure health checks
- Error tracking and alerting
- Resource utilization metrics
- Structured logging with correlation IDs

**Recommended Analytics:**
- User analytics and insights (where applicable)
- Business metrics tracking
- Performance benchmarking

---

## 👥 Standard Team Structure

| Team | Focus Area | Responsibilities |
|------|------------|------------------|
| **Frontend** | UI/UX Development | React components, responsive design, user experience |
| **Backend** | API & Services | Microservice development, database design, business logic |
| **DevOps** | Infrastructure | Kubernetes management, CI/CD, monitoring, security |
| **QA** | Quality Assurance | Automated testing, regression testing, quality gates |

---

## 🤝 Contributing Guidelines

**For all Authism organization projects:**

1. **Follow the [Conventional Commits](https://www.conventionalcommits.org/en/v1.0.0/) standard for all commit messages**
2. Familiarize yourself with the monorepo structure and Turborepo commands
3. Follow the established coding standards for each language
4. Write comprehensive tests for new features within their respective service directories
5. Submit pull requests for code review; `CODEOWNERS` will automatically assign reviewers
6. Update documentation for any architectural changes
7. Ensure all security standards are met before deployment

---

## 📋 Repository Performance Considerations

For massive projects with millions of files and years of history, `git` operations can become slow. This is a long-term concern (5+ years) that we monitor across all repositories. Solutions include:
- Regular repository maintenance
- Git LFS for large files
- Shallow clones for CI/CD when appropriate
- Custom tooling development if needed (following patterns from Google/Meta)

---

## 🔧 Technology Stack Reference

### Languages & Frameworks
- **Rust**: Primary backend language (Actix Web framework)
- **TypeScript + Bun**: Secondary backend choice
- **TypeScript**: Frontend development (Next.js, React)
- **Additional Options**: Python/FastAPI, Go/Gin, Java/Spring

### Infrastructure & Build Tools
- **Kubernetes**: Container orchestration
- **Docker**: Application containerization
- **Turborepo**: Monorepo build system and orchestration
- **GitHub Actions**: Continuous integration/deployment
- **Nginx**: Reverse proxy and load balancing
- **PostgreSQL**: Primary database
- **Redis**: Caching and session management
- **RabbitMQ**: Message queuing

This architecture is **"negative-aware"** - we acknowledge and proactively solve known challenges, which is the hallmark of a great engineering strategy.
