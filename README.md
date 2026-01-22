## Architecture

- AWS EC2 (Ubuntu)
- Self-hosted GitHub Actions runner installed on EC2
- Docker Compose orchestrates:
  - Flask application container
  - MySQL database container
- GitHub Actions triggers on push to `main` and deploys directly to EC2

## CI/CD Flow

1. Developer pushes code to GitHub
2. GitHub Actions workflow runs on EC2 self-hosted runner
3. Docker images are built on the instance
4. Docker Compose updates running containers
5. Health checks verify successful deployment

## Key Challenges Solved

- Handled MySQL readiness using retry logic to avoid container crashes
- Prevented container name and port conflicts in repeated deployments
- Managed disk exhaustion on small EC2 instances
- Ensured idempotent deployments with Docker Compose
- Separated application and database concerns securely
