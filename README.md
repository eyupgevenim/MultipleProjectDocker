    Deployment Multiple .Net Core Project in Docker
- docker-compose
- multi-stage build in docker-compose
- Docker container can only access internet
- Environment variables in docker-compose file
- Docker environment variables as appsettings.json

You need to start it with the following CLI command:
```console
docker-compose -f docker-compose.yml -f docker-compose.dev.yml up --build
