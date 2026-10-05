# VESTA Development Instructions

## Project

VESTA — "Your Style. Your Story."

VESTA is a personalized fashion platform combining:

- personal style profiles
- product discovery
- outfit recommendations
- digital wardrobe
- personalization
- smart sizing
- weather-aware styling
- virtual try-on
- computer vision

The project is being developed incrementally as a portfolio-grade software product.

## Architecture

VESTA uses a separated frontend/backend architecture.

### Frontend

- React
- TypeScript
- Vite
- Tailwind CSS

### Backend

- Java 21
- Spring Boot 4.1.x
- Maven
- Spring Web
- Spring Data JPA
- Hibernate
- Spring Security when authentication is implemented
- REST APIs

### Database

- MySQL 8.4 LTS
- Database migrations will be introduced before production data is created.

### Infrastructure

- Docker
- Docker Compose
- GitHub Actions

## General Engineering Rules

1. Make small, focused changes.
2. Do not implement features that were not explicitly requested.
3. Do not introduce unnecessary dependencies.
4. Do not invent APIs, database relationships, or business rules.
5. Prefer maintainable and readable code over clever code.
6. Keep business logic out of controllers.
7. Use appropriate DTOs instead of exposing persistence entities directly through APIs.
8. Validate external input.
9. Never hardcode passwords, API keys, tokens, or other secrets.
10. Use environment-based configuration for secrets and environment-specific values.
11. Handle errors consistently.
12. Write tests for meaningful business logic.
13. Keep frontend and backend responsibilities clearly separated.
14. Do not create microservices unless there is a demonstrated architectural reason.
15. Avoid premature optimization.

## Backend Rules

Use a modular package structure.

Prefer:

Controller
→ Service
→ Repository
→ Database

Use DTOs at API boundaries.

Controllers should handle HTTP concerns.

Services should contain application/business logic.

Repositories should handle persistence.

Use constructor injection.

Use Bean Validation for request validation.

Use centralized exception handling.

Use appropriate HTTP status codes.

## Frontend Rules

Use TypeScript rather than JavaScript.

Keep reusable UI components separate from page-level components.

Keep API communication inside a dedicated API/service layer.

Avoid putting large amounts of business logic directly inside JSX.

Keep components focused and reusable.

Use responsive design.

Accessibility should be considered for interactive UI.

## Database Rules

Use relational modeling appropriate for MySQL.

Avoid unnecessary duplication.

Use foreign keys where appropriate.

Use indexes deliberately.

Do not store derived values unless there is a clear reason.

Database schema changes must be explicit and reviewable.

## Security Rules

Security is part of the design, not an afterthought.

Never commit secrets.

Validate and sanitize external input where appropriate.

Authentication and authorization must be implemented through established Spring Security mechanisms.

Do not implement custom cryptography.

Do not expose sensitive user information through APIs.

## AI / Recommendation Rules

VESTA must not use fake AI claims.

If the application displays a score, confidence, recommendation, or explanation, there must be an actual mechanism behind it.

For example:

"94% style match"

must correspond to a real scoring model or algorithm.

AI-generated recommendations must remain explainable where practical.

Body measurements and computer-vision results must be presented as estimates unless accuracy has been properly established.

## Development Workflow

VESTA is built incrementally.

For each task:

1. Understand the requested change.
2. Inspect existing code.
3. Make the smallest appropriate implementation.
4. Run relevant tests.
5. Verify the application builds.
6. Report what changed.
7. Identify any remaining issues.

Do not modify unrelated files.

## AI Coding Workflow

AI coding assistants are used as development tools, not as autonomous architects.

The developer must understand and review generated code.

Do not generate large amounts of speculative code.

Prefer small, verifiable changes.

Do not assume future requirements.

When an architectural decision is required, explain the options before implementing it.

## Git

Use meaningful commit messages.

Preferred format:

type: short description

Examples:

feat: add user profile API

fix: handle invalid product request

docs: add architecture decision record

chore: configure backend project

refactor: simplify recommendation service

Keep commits focused.

## Current Development Priority

The initial implementation should focus on:

1. Project foundation
2. Backend foundation
3. Frontend foundation
4. Frontend/backend connectivity
5. Database foundation
6. Authentication
7. User profile
8. Style profile
9. Product catalog
10. Recommendation engine

Do not implement advanced computer vision or virtual try-on during the initial foundation phase.
