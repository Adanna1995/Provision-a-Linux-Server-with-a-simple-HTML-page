# Provision-a-Linux-Server-with-a-simple-HTML-page
Here's a detailed breakdown of how i achieved this task:


Task 1: Provisioning the Server

- i created an account on Amazon Web Services (AWS) and provision a Linux server ensuring i was well within the free tier.
- i used Amazon Linux .
- i successfully provisioned a Linux instance on AWS.


Task 2: Web Server Setup

- Web Server: We installed Nginx (httpd) as our web server on our terminal by:
i. i Updated the package index:
sudo yum update -y

ii. then install Nginx:
sudo yum install nginx 

iii. went ahead to the start service
sudo systemctl start nginx

iv. Enabled Nginx to start automatically on boot:
sudo systemctl enable nginx

v. Verified that Nginx is running:
sudo systemctl status nginx

3. we then went ahead to configure Nginx to serve our website.
sudo nano /etc/nginx/conf.d/mywebsite.conf
an editable file was provived where i filled and configure my nginx like this
server {
    listen 80;
    server_name pamelaaa.me;

    root /var/www/mywebsite;
    index index.html index.htm;

    location / {
        try_files $uri $uri/ =404;
    }

    error_page 500 502 503 504 /50x.html;
    location = /50x.html {
        root /usr/share/nginx/html;
    }
}


   



2. Save the changes with ctrl+O, then Enter then ctrl +X to exit the editable page                                                                                                                                  


After updating the configuration file, try starting the Nginx service again:



bash
sudo systemctl start nginx.service



Your Nginx server should now be serving your website from the /var/www/mywebsite directory.


Task 3: HTML Page Deployment

- HTML Page Creation: You created a simple HTML page (A.html) with contents such as ;
- My name. Anuebunwa Adanna
A project title: “Welcome to Anuebunwa adanna Landing Page.”
A brief description of your project.
Your full bio with every interesting information about you.
- HTML Page Deployment: We deployed the HTML page to the /var/www/html directory on the server.


Task 4: Networking

- HTTP Traffic Configuration: We configured the security group to allow HTTP traffic on port 80.This was done in the security section of my instance.
- Public IP Address: We obtained the public IP address of the server.

public ip: 51.20.89.35

