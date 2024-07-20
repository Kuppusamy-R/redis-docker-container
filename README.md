# Redis Docker Compose Setup

This repository contains a `docker-compose.yml` file to set up a Redis server with a specific password and port.

## docker-compose.yml

```yaml
version: '3.8'

services:
  redis:
    image: redis:latest
    container_name: redis_server
    ports:
      - "6379:6379"  # Change the first "6379" to your desired host port if needed
    environment:
      - REDIS_PASSWORD=yourpassword  # Replace 'yourpassword' with your desired password
    command: [
      "redis-server",
      "--requirepass", "yourpassword",  # Ensure the password matches the one set above
      "--port", "6379"  # Change '6379' to your desired port if different
    ]
    volumes:
      - redis_data:/data

volumes:
  redis_data:
```

# Explanation

## version
Specifies the version of the Docker Compose file format.

## services
Defines the services that will be run.

### redis
Defines the Redis service.

- **image**: Specifies the Docker image to use (in this case, the latest Redis image).
- **container_name**: Names the container (`redis_server`).
- **ports**: Maps the host port to the container port (`6379` in this example).
- **environment**: Sets environment variables (`REDIS_PASSWORD` is used to set the password for Redis).
- **command**: Specifies the command to run Redis with the required password and port.
- **volumes**: Defines a volume to persist Redis data (`redis_data`).

## volumes
Declares the volume used by the Redis service.
