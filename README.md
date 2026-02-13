# Mac Mini Server Setup Guide
1. Initial Server Setup

Foundation: Installed OrbStack as a lightweight Docker alternative on macOS.
Linux Environment: Created an Ubuntu 24.04 LTS (arm64) machine inside OrbStack to act as the server host.

Coolify Installation: Ran the following command inside the Ubuntu terminal to install the management dashboard:
curl -fsSL https://cdn.coollabs.io/coolify/install.sh | sudo bash

Networking: Set up Tailscale on the Mac Mini to provide a secure, persistent IP (100.118.245.114) for remote access.
Public Access: Initiated a Cloudflare Tunnel to bridge api.leviv.cool to the local Node.js port (3000).

2. Deploying a New App Remotely
Manage everything via your Tailscale IP without being on your home Wi-Fi.

Access the Dashboard: Open your browser and go to http://100.118.245.114:8000.

Create New Project: Navigate to Projects > Default > + New.

Connect Code: * Select Public Repository for instant setup.

Paste your GitHub URL (e.g., https://github.com/leviv/new-project).

Configure Build: * Ensure Nixpacks is selected (it will auto-detect Node.js, Python, Go, etc.).

Set the Port to match your app's code (usually 3000).

Environment Variables: Add any required keys or DATABASE_URL in the Environment Variables tab.

Set Domain: * For Private Use: Set the domain to http://100.118.245.114:YOUR_PORT.

For Public Use: Add a new Public Hostname in your Cloudflare Tunnel dashboard pointing to the new local port.

Deploy: Click Deploy and watch the logs.
