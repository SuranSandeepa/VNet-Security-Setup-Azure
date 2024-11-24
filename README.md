# VNet-Security-Setup-Azure

This repository contains the necessary instructions for setting up a secure network within Azure, including installing and configuring Nginx on an Ubuntu VM within the Azure Virtual Network (VNet). Below are the steps to install and configure Nginx on an Ubuntu VM hosted on Azure.

## Steps to Install and Configure Nginx on Ubuntu (VM)

### 1. **Access the VM Using Azure Bastion**
To access the VM securely, use Azure Bastion. Follow these steps to connect to your VM:
   - Go to the Azure portal.
   - Navigate to **Bastion** under your created VNet (e.g., `vnet-demo-network-Bastion`).
   - Click **Connect**.
   - Choose **SSH** as the authentication type.
   - Use your **SSH private key** (e.g., `.pem` file) to authenticate.
   - Enter the username (`azureuser`) and select the private key you downloaded when you created the VM.
   - Click **Connect**. This will open a terminal session on the VM.

### 2. **Update the Ubuntu System**
Once connected to your VM, it's important to update the package list and upgrade existing packages:
```bash
sudo su -
sudo apt update
sudo apt upgrade -y
```

### 3. Install Nginx
Now, install Nginx on the Ubuntu VM:
```bash
sudo apt install nginx -y
```

### 4. Start and Enable Nginx
After installation, start the Nginx service and enable it to start on boot:
```bash
sudo systemctl start nginx
sudo systemctl enable nginx
```

### 5. Create and Configure the HTML File
Create a simple static HTML page that will be served by Nginx. You can edit the default HTML file or create a new one:
```bash
sudo vim /var/www/html/index.html
```
Add your HTML content to this file. You can find the HTML code used in this project in the repository. If you'd like to see the exact HTML content I used, you can access it directly in the index.html file of this repository
Save and exit the editor by pressing Esc then typing :wq and pressing Enter.

### 6. Restart Nginx to Apply Changes
To ensure Nginx picks up the changes to the HTML file, restart the Nginx service:

```bash
sudo systemctl restart nginx
```
### 7. Verify Nginx Installation
To verify that Nginx is serving the page correctly, run the following command from the Bastion terminal:

```bash
curl localhost:80
```


