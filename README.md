# n8n with Cloudflare Tunnel

This repository contains a Docker Compose setup for running n8n with Cloudflare as a tunneling service. n8n is a workflow automation tool that allows you to connect different services and APIs. Cloudflared exposes local servers behind NATs and firewalls to the public internet over secure tunnels.

## Prerequisites

Before you begin, ensure you have the following configured:
- Docker: [Get Docker](https://docs.docker.com/get-docker/)
- Docker Compose: [Install Docker Compose](https://docs.docker.com/compose/install/)
- [Cloudflare Account](https://cloudflare.com)

## Setup

1. **Clone the Repository**

   Clone this repository to your local machine:
   ```bash
   git clone https://github.com/joffcom/n8n-cloudflare.git
   ```

2. **Cloudflare Configuration**

   - Access the Tunnel configuration page in Cloudflare under Zero Trust > Networks > Tunnels
   - Click Create Tunnel and select `Cloudflared` as the Connector
   - Give your tunnel a name, This name is used for you to identify the tunnel and won't be part of the domain
   - Copy your access token and put it in the `.env` file replacing `your_tunnel_token`
   - Configure your subdomain place this in the `.env` file replacing `https://n8n.your-domain.com`
   - For the Service select `http` and set the url to `n8n:5678` this is used for the tunnel routing.

3. **Configure n8n**

   Optionally, you can configure n8n by modifying environment variables in the `docker-compose.yml` file under the `n8n` service.

## Running the Application

To run n8n with Cloudflare, use the following command:

```bash
docker compose up -d
```

This command will start both n8n and Cloudflared services. Cloudflared will provide a URL that tunnels to your n8n instance.

## Accessing n8n

After running the Docker Compose command you can access n8n by navigating to the URL configured in Cloudflare in your web browser.

## Stopping the Application

To stop the n8n and Cloudflared services, use:

```bash
docker compose down
```
