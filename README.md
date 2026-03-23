# Homelab

GitOps source of truth for applications running via Docker on my home server, managed by [doco-cd](https://github.com/kimdre/doco-cd), a lightweight GitOps controller for Docker Compose.

## Overview

This repository defines all the Docker Compose stacks deployed on my homelab Docker VM. Changes pushed to `main` are automatically picked up and applied by doco-cd, making the repo the single source of truth for what runs on the server. Secrets are injected at deploy time from [1Password](https://1password.com/).

## Initial Setup

1. SSH into server
2. Create the secret directory and token file:

   ```bash
   mkdir -p /root/.doco-cd
   echo "<1password-service-account-token>" > /root/.doco-cd/1pw_token
   ```

3. Clone the repo:

   ```bash
   git clone https://github.com/cleversource/homelab
   ```

4. Deploy the bootstrap compose stack:

   ```bash
   cd ~/homelab/dococd
   docker compose up -d
   ```

From this point on, *everything* is self-managing.
