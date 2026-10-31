# Career Copilot — Full-stack MVP

A backend-connected job application tracker built with Java 17, Spring Boot, Spring Data JPA, and H2/PostgreSQL. The frontend is the existing responsive Career Copilot MVP; its source is available in the companion project ZIP.

## Run locally
Requirements: Java 17+ and Maven 3.9+.

```bash
cd career-copilot/backend
mvn spring-boot:run
```

Open http://localhost:8080.

## Run with PostgreSQL
Requirements: Docker Desktop / Docker Engine with Compose.

```bash
cd career-copilot/backend
docker compose up --build
```

Then open http://localhost:8080.

## API
| Method | Endpoint | Purpose |
|---|---|---|
| GET | `/api/health` | Health check |
| GET | `/api/workspace` | Load workspace |
| PUT | `/api/workspace` | Persist workspace snapshot |
| DELETE | `/api/workspace` | Clear workspace |

The workspace snapshot contains applications, profile settings, and activity. The API validates that `jobs` is an array and limits a workspace to 2,000 applications.

## Stack
- Java 17, Spring Boot 3.4
- Spring Web, Spring Data JPA
- H2 for local development
- PostgreSQL 16 for Docker
- Docker Compose

## Important limitations
This is a single-workspace demo without authentication or per-user isolation. Do not deploy publicly with personal data until authentication, authorization, HTTPS, secret management, backups, rate limits, and tests are added. Job discovery, resume parsing, and AI ranking are not yet implemented. The UI uses localStorage as a fallback and syncs with the backend when available.

## Next milestones
1. Add Spring Security and per-user workspaces.
2. Normalize application/profile/activity tables and add migrations.
3. Add resume parsing and AI-based skills-to-job matching.
4. Integrate authorized job sources.
5. Add automated tests and CI.
