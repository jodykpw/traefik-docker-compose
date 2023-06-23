# 🐳 Traefik Docker Compose Example

This repository provides a basic example of using Traefik as a reverse proxy with Docker Compose.

## 🛠️ Prerequisites

- Docker Engine
- Docker Compose

## ⚙️ Optional: Traefik Dashboard Domain and IP Whitelist

1. If you wish to access the Traefik dashboard using a custom domain and restrict access to specific IP addresses, follow these additional steps:

2. Obtain a registered domain name for accessing the Traefik dashboard. This domain will be used to monitor and manage the routing and backend services.

3. Configure the domain name to point to the server where you'll be deploying Traefik. This typically involves setting up DNS records, such as an A record or CNAME record, to direct traffic to the appropriate IP address.

4. Additionally, to enforce the IP whitelist, it is recommended to configure your server's firewall or network infrastructure to allow incoming connections only from the specified IP addresses.

## 📚 Usage

1. 📦 Clone the repository:

    ```shell
    git clone https://github.com/jodykpw/traefik-docker-compose.git
    cd traefik-docker-compose
    ```

2. Before running the Traefik Docker Compose setup, you need to create Docker volumes to store the Traefik configuration and SSL/TLS certificates. Follow the steps below to create the required volumes:

  - By using Docker volumes, you ensure that the Traefik configuration and certificates are persistent and can be easily managed and backed up.

  - Please note that you need appropriate permissions to create Docker volumes on your system. If you encounter any permission issues, you may need to run the above commands with elevated privileges (e.g., using sudo).

  - Make sure to map these volumes to the appropriate paths in your docker-compose.yml file for Traefik to access the configuration and certificate files.

    2.1. Create a Docker volume for Traefik configuration:

    Run the following command to create the Docker volume:

    ```bash
    docker volume create traefik_config
    ```

    2.2. Create a Docker volume for Traefik certificates:

    Run the following command to create the Docker volume:

    ```bash
    docker volume create traefik_certs
    ```      

3. Creating a Docker Network for Traefik

  - To ensure proper communication between Traefik and other services running in Docker containers, it is recommended to create a dedicated Docker network. Follow the steps below to create the network:

  - Please note that you need appropriate permissions to create Docker networks on your system. If you encounter any permission issues, you may need to run the above commands with elevated privileges (e.g., using sudo).

  - Make sure to configure your other services to connect to the traefik_network in their respective Docker Compose files or when running the containers.

    Run the following command to create a Docker network:
      
    ```bash
    docker network create traefik
    ```     

4. ⚙️ Customize the Traefik configuration:

- The traefik.yml file is used to define the main configuration for Traefik. This file contains settings related to entry points, routing, load balancing, middleware, and more.
- Modify the configuration according to your requirements. Pay attention to labels, entry points, backend services, and any additional settings you need.
- Copy the traefik.yml file to the directory /var/lib/docker/volumes/traefik_config/_data while executing the command as the root user.


5. ⚙️ Customize the Dynamic configuration

- The dynamic.config.yml file allows you to define dynamic configurations for Traefik. This file is useful for making runtime changes to the Traefik configuration without restarting the container. 
- Copy the dynamic.config.yml file to the directory /var/lib/docker/volumes/traefik_certs/_data while executing the command as the root user.


6. ⚙️ Customize the sample service configuration:

- Copy the sample `docker-compose.yml.example` file:
  
  ```bash
  cp docker-compose.yml.example docker-compose-prod.yml
  ```

- Open the docker-compose file in a text editor.
- Modify or add new services according to your application needs. Make sure to configure the necessary labels to enable routing and connectivity with Traefik.

7. 🚀  Start the Traefik reverse proxy and services:

    ```bash
    docker-compose -f docker-compose-prod.yml up -d
    ```

8. 🌐 Access your services through Traefik:

- Open a web browser.
- Visit https://your-domain to access the Traefik dashboard and monitor the routing and backend services.

## 🏋️ Advanced Configuration

For advanced configuration options and customization of Traefik, please refer to the official Traefik documentation. It provides detailed information and examples to help you tailor Traefik to your specific requirements.

Visit the official Traefik documentation for more information:

📚 [Traefik Documentation](https://doc.traefik.io/traefik/)

The Traefik documentation covers various topics such as:

- Routing and Load Balancing
- TLS and HTTPS Configuration
- Middlewares and Filters
- Circuit Breakers and Retries
- Observability and Metrics
- And much more!

Take advantage of the comprehensive documentation to explore additional features and advanced configuration options available in Traefik.

If you have specific questions or need further assistance, the Traefik community is also a great resource for support and discussions. Feel free to engage with the community through forums, chat platforms, or GitHub repositories.

Happy exploring and customizing Traefik according to your needs!

## 📄 License

MIT / BSD

## 🇬🇧🇭🇰 Author Information

* Author: Jody WAN
* Linkedin: https://www.linkedin.com/in/jodywan/
* Website: https://www.jodywan.com
