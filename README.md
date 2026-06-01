<div align="center">
  <h2>
    <img src="https://cdn.nodeimage.com/i/NXz3ah3zTwikq3AdQOU0dYw3uyaBiGVj.webp" width="40" height="40" style="vertical-align: middle;"/> 
    nodejs-argo Tunnel Proxy
  </h2>
  nodejs-argo is a powerful Argo tunnel deployment tool designed specifically for PaaS platforms and playground/toy environments. It supports multiple proxy protocols (VLESS, VMess, Trojan, etc.) and integrates Nezha Probe functionality.

---

Telegram Communication & Feedback Group: https://t.me/eooceu
</div>

## Solemn Declaration
* As of October 29, 2025, at 15:45, this project has modified its open-source license and includes the following specific requirements:
* This project is strictly for personal use. Commercial use is forbidden (including but not limited to: YouTube, Bilibili, TikTok, Facebook, etc.).
* It is forbidden to create new projects by copying this code into your own repository for commercial purposes.
* Please abide by local laws and regulations; using this tool as a public proxy or abusing it is strictly prohibited.
* Legal action will be pursued against anyone who violates the above terms.

## Description (Please read carefully before deployment)

* This project is built for Node.js environments on PaaS platforms and playground/toy servers. It deploys nodes via Argo tunnels and features optional integration with Nezha Probe v0 or v1.
* For Node toy platforms, you only need to upload `index.js` and `package.json`. Upload the `Dockerfile` only if your PaaS platform requires Docker deployment.
* Leaving the `ARGO_DOMAIN` and `ARGO_AUTH` variables blank will enable a temporary tunnel. Providing values will use a fixed tunnel instead.
* Nezha v0/v1 is optional. When the Nezha port matches one of the following: {443, 8443, 2096, 2087, 2083, 2053}, TLS will be enabled automatically.

## 📋 Environment Variables


| Variable Name | Required | Default Value | Description |
|---|---|---|---|
| UPLOAD_URL | No | - | Subscription upload address |
| PROJECT_URL | No | https://www.google.com | Domain name assigned to the project |
| AUTO_ACCESS | No | false | Whether to enable automatic access for keep-alive |
| PORT | No | 3000 | HTTP service listening port |
| ARGO_PORT | No | 8001 | Argo tunnel port |
| UUID | No | 89c13786-25aa-4520-b2e7-12cd60fb5202 | User UUID |
| NEZHA_SERVER | No | - | Nezha dashboard domain |
| NEZHA_PORT | No | - | Nezha port |
| NEZHA_KEY | No | - | Nezha secret key |
| ARGO_DOMAIN | No | - | Argo fixed tunnel domain |
| ARGO_AUTH | No | - | Argo fixed tunnel token/auth |
| CFIP | No | www.visa.com.tw | Cloudflare optimized domain or IP for nodes |
| CFPORT | No | 443 | Node port |
| NAME | No | Vls | Node name prefix |
| FILE_PATH | No | ./tmp | Runtime directory |
| SUB_PATH | No | sub | Subscription path |

## 🌐 Subscription Addresses

- Standard Port: `https://your-domain.com/sub`
- Non-standard Port: `http://your-domain.com:port/sub`

---

## 🚀 Advanced Usage

### Installation

```bash
# Global installation (Recommended)
npm install -g nodejs-argo

# Or using yarn
yarn global add nodejs-argo

# Or using pnpm
pnpm add -g nodejs-argo
```

### Basic Usage

```bash
# Run directly (using default configurations)
nodejs-argo

# Run using npx
npx nodejs-argo

# Run with environment variables set
PORT=3000 npx nodejs-argo
```

### Environment Variable Configuration

You can use a `.env` file to configure environment variables for running.

Or set them directly in the command line:

```bash
export UPLOAD_URL="https://your-merge-sub-domain.com"
export PROJECT_URL="https://your-project-domain.com"
export PORT=3000
export UUID="your-uuid-here"
export NEZHA_SERVER="nz.your-domain.com:8008"
export NEZHA_KEY="your-nezha-key"
```

## 📦 Usage as an npm Module

```javascript
// CommonJS
const nodejsArgo = require('nodejs-argo');

// ES6 Modules
import nodejsArgo from 'nodejs-argo';

// Start service
nodejsArgo.start();
```

## 🔧 Running in the Background

### Using screen (Recommended)
```bash
# Create a screen session
screen -S argo

# Run the application
nodejs-argo

# Press Ctrl+A then D to detach the session
# Reconnect using: screen -r argo
```

### Using tmux
```bash
# Create a tmux session
tmux new-session -d -s argo

# Run the application
tmux send-keys -t argo "nodejs-argo" Enter

# Detach the session: tmux detach -s argo
# Reconnect using: tmux attach -t argo
```

### Using PM2
```bash
# Install PM2
npm install -g pm2

# Start the application
pm2 start nodejs-argo --name "argo-service"

# Manage the application
pm2 status
pm2 logs argo-service
pm2 restart argo-service
```

### Using systemd (Linux System Service)
```bash
# Create the service file
sudo nano /etc/systemd/system/nodejs-argo.service
```

```ini
[Unit]
Description=Node.js Argo Service
After=network.target

[Service]
Type=simple
User=root
WorkingDirectory=/root/test
Environment=ARGO_PORT=8080
Environment=PORT=3000
ExecStart=/usr/bin/npx nodejs-argo
Restart=always
RestartSec=10

[Install]
WantedBy=multi-user.target
```

```bash
# Start the service
sudo systemctl start nodejs-argo
sudo systemctl enable nodejs-argo
```

## 🔄 Updates

```bash
# Update globally installed package
npm update -g nodejs-argo

# Or reinstall
npm uninstall -g nodejs-argo
npm install -g nodejs-argo
```

## 📚 More Information

- [GitHub Repository](https://github.com/eooce/nodejs-argo)
- [npm Package Page](https://www.npmjs.com/package/nodejs-argo)
- [Issue Feedback](https://github.com/eooce/nodejs-argo/issues)

---

## Sponsorship
* Thanks to [VPS.Town](https://vps.town) for sponsoring. <a href="https://vps.town" target="_blank"><img src="https://vps.town/static/images/sponsor.png" width="30%" alt="https://vps.town"></a>

* Thanks to [ZMTO](https://zmto.com/?affid=1548) for sponsoring premium dual-ISP VPS.
