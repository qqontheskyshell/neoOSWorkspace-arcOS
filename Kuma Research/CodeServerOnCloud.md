Here's a complete **step-by-step guide** to install **code-server** (VS Code in the browser) on a **Google Cloud Compute Engine VM**:

***

## Step 1: Create a Google Cloud Project & Enable APIs

1. Go to the [Google Cloud Console](https://console.cloud.google.com)
2. **Create or select a project**:
   ```markdown
   gcloud config set project YOUR_PROJECT_ID
   ```
3. **Enable Compute Engine API**:
   ```markdown
   gcloud services enable compute.googleapis.com
   ```

***

## Step 2: Create a VM Instance

### Option A: Via GCP Console (UI)
1. Go to **Compute Engine > VM instances**
2. Click **Create Instance**
3. Configure:
   - **Name**: `codeserver-vm`
   - **Region/Zone**: e.g., `us-central1-f`
   - **Machine type**: Minimum **2 vCPU, 4 GB RAM** (recommended: `e2-medium` or better)[4]
   - **Boot disk**: Ubuntu 20.04 LTS or 22.04 LTS[1]
   - **Firewall**: Check **Allow HTTP traffic** and **Allow HTTPS traffic**

### Option B: Via gcloud CLI
```markdown
gcloud compute instances create codeserver-vm \
  --machine-type=e2-medium \
  --zone=us-central1-f \
  --image-family=ubuntu-2204-lts \
  --image-project=ubuntu-os-cloud \
  --boot-disk-size=50GB \
  --allow-http
```

***

## Step 3: SSH into the VM

```markdown
gcloud compute ssh codeserver-vm --zone=us-central1-f
```

***

## Step 4: Install code-server

Run these commands inside the VM:

```markdown
# Update system
sudo apt update && sudo apt upgrade -y

# Install code-server using the automatic installer
curl -fsSL https://code-server.dev/install.sh | sh

# Or download manually (alternative)
VERSION=4.96.2  # check latest at https://github.com/coder/code-server/releases
wget https://github.com/coder/code-server/releases/download/v$VERSION/code-server-$VERSION-linux-x64.tar.gz
tar -xvzf code-server-$VERSION-linux-x64.tar.gz
cd code-server-$VERSION-linux-x64
```

***

## Step 5: Run code-server on all interfaces

**Important**: You must bind to `0.0.0.0` to access from outside:[1]

```markdown
# Set password (change 'mypassword' to your choice)
PASSWORD=mypassword PORT=8080 code-server --host 0.0.0.0
```

Or run it as a **systemd service** (recommended for persistence):

```markdown
# Create systemd service
sudo tee /etc/systemd/system/code-server.service > /dev/null <<EOF
[Unit]
Description=code-server
After=network.target

[Service]
Type=simple
User=$USER
ExecStart=/home/$USER/.local/bin/code-server --host 0.0.0.0 --port 8080
Restart=always
Environment="PASSWORD=mypassword"

[Install]
WantedBy=multi-user.target
EOF

# Enable and start service
sudo systemctl daemon-reload
sudo systemctl enable code-server
sudo systemctl start code-server
```

***

## Step 6: Open Firewall Port (if needed)

If you didn't allow HTTP during VM creation:

```markdown
gcloud compute firewall-rules create allow-code-server \
  --allow tcp:8080 \
  --source-ranges 0.0.0.0/0 \
  --target-tags http-server \
  --description "Allow code-server traffic"
```

***

## Step 7: Access code-server

1. Get your VM's **external IP**:
   ```markdown
   gcloud compute instances describe codeserver-vm \
     --zone=us-central1-f \
     --format='get(networkInterfaces.accessConfigs.natIP)'
   ```

2. Open in browser:
   ```
   http://YOUR_EXTERNAL_IP:8080
   ```

3. Enter your password when prompted

***

## Optional: Add HTTPS with Let's Encrypt

For production use, add a domain and HTTPS:

```markdown
sudo apt install certbot python3-certbot-nginx -y
sudo certbot --nginx -d yourdomain.com
```

***

## Quick Reference Table

| Step | Action | Command/Note |
|------|--------|--------------|
| 1 | Enable API | `gcloud services enable compute.googleapis.com` [2] |
| 2 | Create VM | `gcloud compute instances create` [4] |
| 3 | SSH | `gcloud compute ssh codeserver-vm` |
| 4 | Install | `curl -fsSL https://code-server.dev/install.sh \|\| sh` [6] |
| 5 | Run | `--host 0.0.0.0` required [1] |
| 6 | Access | `http://EXTERNAL_IP:8080` [1] |

***

This setup works great for iPad development with Blink Shell access to GitHub repos, matching your workflow. The VM can run continuously or be stopped when not in use to save costs.

Sources
[1] Code server (Visual Studio Code) on Google Cloud Engine https://stackoverflow.com/questions/61829412/code-server-visual-studio-code-on-google-cloud-engine-err-connection-refused
[2] Installation and Setup | Cloud Deployment Manager https://docs.cloud.google.com/deployment-manager/docs/step-by-step-guide/installation-and-setup
[3] Code-Server (VSCode) on Google Cloud Run : r/googlecloud - Reddit https://www.reddit.com/r/googlecloud/comments/gsopvr/codeserver_vscode_on_google_cloud_run/
[4] doc/admin/install/google_cloud.md - code-server - GitLab https://gitlab.b-data.ch/coder/code-server/-/blob/1.32.0-245/doc/admin/install/google_cloud.md
[5] coder/code-server: VS Code in the browser - GitHub https://github.com/coder/code-server
[6] Install code-server: OS Instructions for VS Code - Coder https://coder.com/docs/code-server/install
[7] HOW TO INSTALL VS CODE ON A CHROMEBOOK AND GOOGLE ... https://www.youtube.com/watch?v=MrSmHQpXBwc
[8] Setting Up a Google Cloud VM for R and Python with VSCode https://peterjohnlambert.com/data-coding/guide-to-setting-up-a-virtual-machine-using-google-cloud-for-applied-economics/
[9] Deploying simple code on Google Cloud | Towards Data Science https://towardsdatascience.com/deploying-simple-code-on-google-cloud-2cb3d50f7d33/
