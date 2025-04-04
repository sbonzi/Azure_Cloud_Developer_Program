# Azure_Cloud_Developer_Program
Cloud Developer Program Using Microsoft Azure

Program : https://udacity.com/enrollment/nd081


1. Introduction
    Prerequisites:
      </> At least 1-3 years of web development experience, preferably programming in Python
      </> Experience creating and managing databases such as SQL Server or PostgreSQL.
      </> Comfortable using Git as a version control system to clone, pull, or push code.
      </> A free or existing Azure account needed to create and provision Azure services

    Concepts: 
      StakeHolders: Your users, Company executives, I.T. Department, Cloud Service provider, Finance Department
      Infrastructure as a Service (IaaS) - removes the expense of up-front costs of hardware, software and test environments
      Platform as a Service (PaaS) - handles networking, provides middleware and development & database tools
      Software as a Service (SaaS) - provides end-users access to online cloud solutions

2. Azure Applications
    Concepts: 
      </> Costs Management, Subscriptions & Resource Groups
      </> Compute Services : VM, App Services, Azure Batch, Azure Functions, Container Instances, Service Fabric, AKS (Kubernetes)
      
    Exercises:
      </> Creating a VM - Create a Linux VM called “linux-vm-west” inside “resource-group-west”. 
                          VM configurations:
                          { 
                            VM Name: "linux-vm-west"
                            Region: West US or the closest region to you that's available
                            Availability Options: No infrastructure redundancy is required.
                            Image: Ubuntu Server (any version)
                            Azure Spot instance: No
                            Size: Standard B1ls
                            Authentication type: Password
                            Username: (any username you choose)
                            Password: (any password you choose)
                            Inbound Port Rules: Allow both 22 and 80
                           }

                         - Clone this repo and navigate to the /L2. Azure Compute Services/Creating_a_Virtual_Machine/ path in the cloned repo
                           > cd "L2. Azure Compute Services/Creating_a_Virtual_Machine/
                         - Use secure copy to copy the web directory from this directory to the VM.
                           > scp -r ./web <USERNAME>@<IPADDRESS>:/home/<USERNAME>
                         - After copying the files to the VM, connect to it and run the command ls to check the web directory is on the VM.
                         - Install python3-env and nginx
                           > sudo apt-get -y update && sudo apt-get -y install nginx python3-venv
                         - Configure nginx to listen for incoming traffic on port 80 and set port 3000 as the proxy.
                           * Navigate to /etc/nginx/sites-avaiable
                           * Remove the default file
                           * Replace it with a file containing:
                              server {
                                listen 80;
                                location / {
                                proxy_pass http://localhost:3000;
                                proxy_http_version 1.1;
                                proxy_set_header Upgrade $http_upgrade;
                                proxy_set_header Connection keep-alive;
                                proxy_set_header Host $host;
                                proxy_cache_bypass $http_upgrade;
                                }
                              }
                           * Saving the file, restart nginx 
                             > sudo service nginx restart 
                          - Change to the web directory and create and activate a virtual env
                          - As a best practice, update pip in a newly created virtual env
                          - Install dependencies from requirements.txt
                          - Run the application and visit the public IP address in your browser. You should see the application running if done correctly.

4. Azure Microservices

5. Azure Migration

6. Azure Performance

7. AZ-204 Certification
