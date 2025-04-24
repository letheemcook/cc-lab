# Portfolio Website - Simple Docker Deployment

This repository contains a simple portfolio website that can be deployed using Docker and Nginx.

## Project Overview

This is a static website portfolio that includes:
- HTML for structure
- CSS for styling (embedded in HTML)
- JavaScript for interactivity
- Nginx for serving the static content

## Local Development

1. You can test the website locally by opening `index.html` in a browser
2. To test with Docker locally:
   ```bash
   # Build the Docker image
   docker build -t portfolio-website .
   
   # Run the container
   docker run -d -p 8080:80 --name portfolio-website-local portfolio-website
   
   # Access the website at http://localhost:8080
   ```

## Deployment

The simplest way to deploy this website is using Docker with Nginx:

1. Make sure Docker is installed on your server:
   ```bash
   # For Ubuntu/Debian
   sudo apt update
   sudo apt install docker.io
   sudo systemctl enable --now docker
   
   # For Amazon Linux/CentOS
   sudo yum update -y
   sudo yum install docker -y
   sudo systemctl enable --now docker
   ```

2. Clone this repository:
   ```bash
   git clone https://github.com/yourusername/portfolio.git
   cd portfolio
   ```

3. Build and run the Docker container:
   ```bash
   docker build -t portfolio-website .
   docker run -d -p 80:80 --name portfolio-website portfolio-website
   ```

4. Your website is now accessible at http://your-server-ip

## Updating the Website

To update your website after making changes:

```bash
# Pull the latest changes (if from git repository)
git pull

# Rebuild and restart the container
docker stop portfolio-website
docker rm portfolio-website
docker build -t portfolio-website .
docker run -d -p 80:80 --name portfolio-website portfolio-website
```

## File Structure

- `index.html`: Main HTML file for the portfolio website
- `script.js`: JavaScript functionality for the website
- `nginx.conf`: Nginx server configuration
- `Dockerfile`: Docker configuration to build the container
- `README.md`: This documentation file

## Troubleshooting

If the website is not accessible, check:
- Docker container is running: `docker ps`
- Server firewall allows incoming connections on port 80
- Check container logs: `docker logs portfolio-website`
