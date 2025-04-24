Self-Healing Infrastructure with Prometheus, Alertmanager, and Ansible

Project Overview

This project demonstrates a self-healing infrastructure using Prometheus, Alertmanager, Ansible, and Flask Webhook to automatically detect and recover from service failures. The system monitors the status of a NGINX service, and when it goes down, Prometheus triggers an alert that is processed by Alertmanager. The webhook then calls an Ansible playbook to restart the service, ensuring high availability.

Objective

Automatically detect service failures and recover them using alerts and automation.

Key Features:

Prometheus monitors the health of NGINX.
Alertmanager triggers alerts based on predefined thresholds.
Flask Webhook receives alerts and triggers an Ansible playbook.
Ansible restarts the NGINX service if it is down.
Tools Used

Prometheus: Monitoring and alerting toolkit
Alertmanager: Handles alerts sent by Prometheus
Ansible: Automation tool to restart the NGINX service
Flask: Python web framework for the webhook service
Docker: For containerizing the application
Docker Compose: To manage multi-container Docker applications
Ubuntu EC2: Used as the deployment environment
Project Architecture

The architecture consists of the following components:

Prometheus: Collects metrics from the NGINX service.
Alertmanager: Manages alert notifications when NGINX goes down.
Flask Webhook: Receives alerts and triggers the Ansible playbook.
NGINX: The sample service being monitored.
Ansible Playbook: Restarts the NGINX service when a failure is detected.
Setup Instructions

Prerequisites

Ensure you have the following tools installed:

Docker
Docker Compose
Git
Clone the Repository

Clone the repository to your local machine:

git clone https://github.com/santhoshreddy1818/self-healing-infra.git
cd self-healing-infra
Run the Project

Start the Docker Containers: Run the following command to start all the containers:

docker-compose up --build -d
This will build and start the Prometheus, Alertmanager, NGINX, Flask Webhook, and Ansible containers.

Verify the Setup:

Visit http://:9090 to view Prometheus status.
Visit http://:5001 to see the Flask Webhook running.
Visit http:// to check NGINX status.
Test the Self-Healing

To test the self-healing system:

Stop the NGINX service:

docker stop $(docker ps -q --filter name=nginx)
Prometheus will detect the failure and trigger an alert, which will be processed by Alertmanager. The Flask webhook will call the Ansible playbook to restart the NGINX service automatically.

Check the logs for confirmation:

docker logs $(docker ps -aqf name=webhook)
Logs and Screenshots

You can find demo logs and screenshots in the screenshots/ folder.

Directory Structure

├── ansible/                # Ansible playbook and configuration
├── docker-compose.yml      # Docker Compose file to define the services
├── prometheus.yml          # Prometheus configuration
├── alertmanager.yml        # Alertmanager configuration
├── webhook.py              # Flask Webhook service
├── Dockerfile              # Dockerfile for the Flask Webhook
├── screenshots/            # Folder for demo screenshots
└── README.md               # Project README
Author

SANTHOSH REDDY
Email: santhoshreddychada6302@gmail.com
GitHub: santhoshreddy1818
College: Alliance University, CSE
EC2 Public IP: 52.204.238.63
