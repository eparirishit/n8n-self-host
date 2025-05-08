# n8n and ngrok Docker Compose

## Overview
This setup runs a self-hosted n8n instance in a Docker container and exposes it to the internet using ngrok. This is useful for testing and using n8n’s webhook features locally, without dealing with complex port forwarding.

## Features
- **n8n**: A node-based workflow automation tool.  
- **ngrok**: Creates secure tunnels to the local instance, enabling external webhooks and access to the n8n interface.

## Prerequisites
- Docker and Docker Compose installed.
- An ngrok account for custom domains.

## Environment Variables
The Docker Compose file references:
- `N8N_BASIC_AUTH_USER`  
- `N8N_BASIC_AUTH_PASSWORD`  
- `NGROK_AUTHTOKEN`
- `NGROK_CUST_DOMAIN_URL`

Set these in a `.env` file or export them directly in your shell before running the containers.

## How to Get a Free ngrok Custom Domain

1. **Sign up for a free ngrok account:**  
   Visit [ngrok.com](https://ngrok.com/) and create a free account.

2. **Get your ngrok authtoken:**  
   After logging in, go to the [Auth Token page](https://dashboard.ngrok.com/get-started/your-authtoken) and copy your token.

3. **Reserve a free custom domain:**  
   - Go to the [Domains](https://dashboard.ngrok.com/domains) under Universal Gateway.
   - Click "New Domain".
   - Copy the full domain name (e.g., `yourname-test.ngrok-free.app`).

4. **Update your `.env` file:**  
   ```
   N8N_BASIC_AUTH_USER=youruser
   N8N_BASIC_AUTH_PASSWORD=yourpassword
   NGROK_CUST_DOMAIN=yourname-test.ngrok-free.app
   NGROK_CUST_DOMAIN_URL=https://yourname-test.ngrok-free.app
   ```

## Usage
1. Place the Docker Compose file and ngrok configuration in the same directory.  
2. Make sure you have set up any required environment variables in your `.env` file.  
3. Run:
   ```bash
   docker-compose up -d
   ```
4. Access n8n via the URL shown in the Docker logs or your reserved ngrok domain.

Use this configuration for local development, testing, and prototyping. For production setups, additional security and scaling measures may be required.