🏗️ Infrastructure Setup: VM, Docker, and Splunk Integration
Project Overview
This lab documents the process of provisioning a Linux Virtual Machine, deploying Splunk Enterprise using Docker containers, and establishing a secure connection for log analysis. This setup serves as the foundation for the Apache Log Analysis project.

Step 1: Virtual Machine Provisioning 🖥️
OS Selection: Deployed a Ubuntu Server instance to act as the host for the Docker environment.

Resource Allocation: Configured the VM with adequate CPU and RAM to handle simultaneous container operations and indexing.

Network Configuration: Set up a static IP and configured firewall rules to allow traffic on port 8000 (Splunk Web) and 8089 (Management).

Step 2: Docker Installation & Configuration 🐋
Repository Setup: Updated the apt package index and installed necessary dependencies for Docker.

Engine Installation: Installed the Docker Engine and Docker Compose to manage multi-container applications.

User Permissions: Added the current user to the docker group to manage containers without sudo privileges, following security best practices.

Step 3: Deploying Splunk via Docker 📊
Image Pull: Pulled the official splunk/splunk image from Docker Hub.

Container Deployment: Ran the container with environment variables to accept the License Agreement and set a secure administrator password.

Command Example: docker run -d -p 8000:8000 -e "SPLUNK_START_ARGS=--accept-license" -e "SPLUNK_PASSWORD=YourSecurePassword" --name splunk splunk/splunk.

Volume Mapping: Configured Docker volumes to ensure data persistence for indexed logs and configuration files.

Step 4: Connecting & Verifying the SIEM ✅
Web Interface Access: Accessed the Splunk GUI via the VM's IP address on port 8000.

Service Verification: Confirmed that the Splunk engine was running correctly by checking container logs and the system health dashboard.

Data Ready: Established the environment for the ingestion of Apache access logs for the forensic analysis phase.

Key Skills Demonstrated 🛠️
Virtualization: Experience managing VM life cycles.

Containerization: Proficiency with Docker and container orchestration.

Linux Administration: Mastery of the command line for system configuration.

Network Security: Managing ports and firewall protocols for secure application access.

🌐 Network & Architecture Diagram
To better understand the flow of data and the isolation of services, here is the architectural breakdown of this lab environment:

Host Layer (Ubuntu VM): Acts as the physical-virtual boundary, providing the kernel and resources (CPU/RAM) for the lab.

Container Engine (Docker): Manages the lifecycle of the Splunk instance, ensuring it is isolated from the host OS for security and portability.

Service Layer (Splunk Image): A lightweight, standalone instance of Splunk Enterprise running inside the container.

Port Mapping (8000:8000): Bridges the VM’s network to the container, allowing me to access the Splunk Web UI from my local browser while keeping the container's internal environment secure.

Data Volume Persistence: Maps a directory on the Ubuntu host to the container’s /opt/splunk/var to ensure that indexed logs are not lost if the container is restarted or updated.
