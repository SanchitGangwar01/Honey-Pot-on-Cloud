

# Honeypot (T-Pot) Deployment on Azure
## Project Made by - Sanchit Gangwar
## Cybersecurity Project

## # Introduction

T-Pot is an open-source honeypot platform that integrates multiple honeypot technologies and visualization tools. Deploying T-Pot on Azure allows for the monitoring and analysis of cyber threats in a cloud environment.

## # Setting Up the Azure Virtual Machine

### Creating the VM

1. **Log into Azure Portal**: Access the [Azure Portal](https://portal.azure.com/).

2. **Create a Virtual Machine**:
   - **Subscription**: Select your subscription.
   - **Resource Group**: Choose or create a resource group.
   - **VM Name**: `TPot-VM`.
   - **Region**: Select an appropriate region.
   - **Image**: `Debian 12`.
   - **Size**: `Standard D2s v3` (2 vCPUs, 8 GB RAM).
   - **Authentication**: SSH public key.
   - **Username**: Your chosen username.
   - **SSH Public Key**: Paste your SSH public key.

   ![Alt text](azure.png)


### Configuring Networking

1. **Network Security Group (NSG) Rules**:
   - Allow inbound traffic on ports `22` (SSH), `64297` (T-Pot Web UI), and `64295` (SSH post-installation).
   ![Alt text](azure resource group.png)

## # Preparing the VM for T-Pot Installation

### System Update and Upgrade

Update and upgrade the system packages:

```bash
sudo apt update && sudo apt upgrade -y
```



### Installing Essential Packages

Install `git`:

```bash
sudo apt install -y git
```


## # Installing T-Pot

### Cloning the T-Pot Repository

1. **Clone the Repository**: Navigate to your home directory and clone the T-Pot Community Edition repository:

   ```bash
   git clone https://github.com/telekom-security/tpotce.git
   ```
   

### Running the Installer

1. **Navigate to the Installer Directory**:

   ```bash
   cd tpotce
   ```


2. **Execute the Installation Script**:

   ```bash
   sudo ./install.sh
   ```
   ![Alt text](tpot_installer.png)


3. **Follow On-Screen Prompts**: During installation, you'll be prompted to:
   - **Select Installation Type**: Choose the standard T-Pot installation or a specialized setup ,i choose standard type.
   - **Create a User**: Set a username and password for accessing the T-Pot web interface.

      ![Alt text](tpot_install_last.png)


4. **Reboot the System**: After installation completes, reboot the VM:

   ```bash
   sudo reboot
   ```


   

## # Accessing T-Pot's Web Interface

1. **Open a Web Browser**: On your local machine.

2. **Navigate to the T-Pot Web UI**: Enter `https://<Public-IP>:64297` in the address bar (replace `<Public-IP>` with your VM's public IP address).

3. **Proceed Past Security Warning**: Due to the self-signed certificate, you'll encounter a security warning. Proceed to the site.

4. **Log In**: Use the credentials set during installation.

      ![Alt text](tpot_menu.png)





## # Exploring T-Pot's Features

T-Pot integrates multiple honeypot technologies and visualization tools, providing a robust platform for monitoring and analyzing cyber threats. Key components include:

### Kibana

Kibana is a data visualization and exploration tool for reviewing logs and metrics. In T-Pot:

- **Dashboard Access**: Navigate to the Kibana section via the T-Pot web interface.

- **Visualizations**: Analyze data through various charts and graphs, aiding in identifying attack patterns and trends.


### Attack Map

The Attack Map provides a real-time, geographical representation of incoming attacks:

- **Visualization**: Observe attack origins and targets on a world map, enhancing situational awareness.

   ![Alt text](attackmap.png)


### CyberChef

CyberChef is a versatile tool for data analysis and manipulation:

- **Features**: Perform tasks such as decoding, encoding, encryption, and data parsing.

   ![Alt text](cyberchef(2).png)


### Elasticvue

Elasticvue is an Elasticsearch GUI for managing and browsing your Elasticsearch clusters:

- **Functionality**: Inspect indices, query data, and monitor cluster health.

   ![Alt text](elastic_curve.png)


### SpiderFoot

SpiderFoot is an open-source intelligence (OSINT) automation tool:

- **Capabilities**: Gather intelligence on IPs, domains, emails, and more, aiding in threat intelligence efforts.

   ![Alt text](spiderfoot(2).png)




##  Conclusion

Deploying T-Pot on Azure provides valuable insights into potential threats targeting your environment. By meticulously documenting the process and observations, you contribute to the broader cybersecurity community's knowledge base.

---
