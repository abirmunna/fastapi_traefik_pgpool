# FastAPI + Traefik + PostgreSQL Replication with PGPool: A Docker Compose Setup

## Project Description

This project sets up a **FastAPI** application running in multiple instances, routed through **Traefik**, and connected to a **PostgreSQL** database with master-replica replication. **PGPool** is used to load balance queries across the database nodes.

## Features

- 🚀 **FastAPI** with multiple instances for load balancing API requests.
- 🔀 **Traefik** for automatic routing and balancing traffic across FastAPI instances.
- 🗄️ **PostgreSQL** with master-slave replication to ensure high availability and data redundancy.
- ⚖️ **PGPool** for load balancing read queries across PostgreSQL replicas.

## Setup

1. Clone this repository.

    ```bash
    git clone <repository-url>
    cd <repository-folder>
    ```

2. Build and start the services.

    ```bash
    docker-compose up --build
    ```

    This will start:

    - Traefik on port 80 for web traffic and 8080 for its dashboard.
    - FastAPI on port 8000 (automatically load-balanced).
    - PGPool on port 5437.
    - PostgreSQL primary on port 5435 and two replicas on 5436 and 5438.

3. Access the Traefik dashboard at:

    ```
    http://localhost:8080
    ```

4. Test the FastAPI service:

    ```
    http://localhost/
    ```

## Important Notes

- Passwords & Sensitive Data: This setup doesn't use an .env file for environment variables like passwords. For production, always store sensitive data securely using environment files or secrets management tools.
- Database Volumes: No persistent volumes are configured for the PostgreSQL database in this demo. Data will be lost when containers are stopped. For production use, mount volumes to persist data.

## Clean Up

To stop and remove the containers, run:

```bash
docker-compose down
```

## Improvements

For a production-ready setup, consider:

- Storing sensitive data (passwords, user details) in an .env file.
- Mounting volumes for the PostgreSQL containers to ensure data persistence.
- Enabling SSL/TLS in Traefik for secure communication.

## Conclusion

This setup is a great way to see how FastAPI, Traefik, PostgreSQL replication, and PGPool work together in a scalable, distributed architecture. While this demo is great for experimentation, always ensure best practices in a production environment.