# Project Compose Proxy

A simple, flexible Docker Compose setup for running a Traefik reverse proxy with dynamic configuration support. This project is designed to make it easy to manage and route traffic to multiple services using Traefik, with configuration files stored in the `dynamic/` directory.

## Features

- Traefik reverse proxy (latest)
- Dynamic configuration via mounted files
- Automatic HTTPS with Let's Encrypt
- HTTP to HTTPS redirection
- Docker provider integration
- Dashboard and health check enabled

## Directory Structure

```
docker-compose.yml
/dynamic
    mealie.example.yml
    portainer.example.yml
    ...
```

## Getting Started

1. **Clone the repository:**
   ```bash
   git clone <your-repo-url>
   cd Project-Compose-Proxy
   ```

2. **Create a `.env` file:**
   Set the following environment variables in a `.env` file at the project root:
   - `STACK_NAME` (e.g., `proxy`)
   - `LE_EMAIL` (your email for Let's Encrypt)
   - `DYNAMIC_DIR` (absolute path to your `dynamic/` directory)
   - `HTTP_PORT` (optional, default: 8080)
   - `HTTPS_PORT` (optional, default: 8443)

   Example:
   ```env
   STACK_NAME=proxy
   LE_EMAIL=your@email.com
   DYNAMIC_DIR=/absolute/path/to/dynamic
   HTTP_PORT=8080
   HTTPS_PORT=8443
   ```

3. **Add or edit dynamic configuration files:**
   Place your Traefik dynamic config files in the `dynamic/` directory. Example files are provided.

4. **Start the proxy:**
   ```bash
   docker compose up -d
   ```

5. **Access the Traefik dashboard:**
   - Visit `http://localhost:8080/dashboard/` (or your configured HTTP_PORT)

## Customization
- Edit or add files in `dynamic/` to define routers, services, and middlewares for Traefik.
- Use the provided example files as templates.

## Volumes
- `${STACK_NAME}-letsencrypt`: Stores Let's Encrypt certificates.
- `${DYNAMIC_DIR}`: Mounts your dynamic configuration directory.

## License

[MIT License](LICENSE)