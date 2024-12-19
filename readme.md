# Akaunting Docker Compose Setup

This repository contains a Docker Compose file to set up an Akaunting instance using the [KuraLabs Docker Akaunting image](https://github.com/samsesh/docker-akaunting). Akaunting is a free, open-source accounting software for small businesses.

## Requirements

- Docker
- Docker Compose

---

## Services Configuration

### `akaunting`
- **Image**: `kuralabs/docker-akaunting:latest`
- **Hostname**: `akaunting`
- **Container Name**: `akaunting`
- **Restart Policy**: `always`
- **Ports**: 
  - `8080:8080` (Adjust as needed for your environment)
- **Environment Variable**: 
  - `MYSQL_ROOT_PASSWORD`: Ensure you replace the default value with a strong, secure password. Use the command below to generate one:
    ```bash
    openssl rand -base64 48
    ```
- **Volumes**:
  - `./data/mysql:/var/lib/mysql`: Persists MySQL data.
  - `./data/logs:/var/log`: Stores application logs.
  - `./data/config:/var/www/akaunting/config`: Holds configuration files for Akaunting.

---

## Usage

1. **Clone this repository**
   ```bash
   git clone https://github.com/samsesh/docker-akaunting.git
   cd docker-akaunting
   ```

2. **Set up the environment**
   - Open the `docker-compose.yml` file and replace `MYSQL_ROOT_PASSWORD` with a secure password.

3. **Start the services**
   ```bash
   docker compose up -d
   ```

4. **Access Akaunting**
   - Navigate to [http://localhost:8080](http://localhost:8080) (or the server's IP/hostname) in your browser.

---

## Donate

If you find this project helpful and would like to support its development, consider donating.  
Visit [donate.samsesh.net](https://donate.samsesh.net) for more information.

---

## Troubleshooting

- Ensure Docker and Docker Compose are correctly installed on your system.
- Verify port `8080` is available and not being used by another application.
- Check the logs for any issues:
  ```bash
  docker logs akaunting
  ```


