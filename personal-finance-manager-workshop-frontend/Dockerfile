# # Use the official Node.js image as a base
FROM node:latest as builder

# Set the working directory in the container
WORKDIR /app

# Copy package.json and package-lock.json files
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy the rest of the application code
COPY . .

# Build the Angular app for production
RUN npm run build

# Use Nginx as a lightweight web server
FROM nginx:stable-alpine

# Remove default NGINX website
RUN rm -rf /usr/share/nginx/html/*

# Copy NGINX configuration file
#COPY nginx.conf /etc/nginx/conf.d/default.conf

# WORKDIR /usr/share/nginx/html

# Copy the built Angular app from the build stage into the nginx directory
COPY --from=builder /app/dist/expense/ /usr/share/nginx/html

# Expose port 4200
EXPOSE 80

# Command to run the nginx server
CMD ["nginx", "-g", "daemon off;"]

# client/Dockerfile
# Use official Node.js image
# Use an official Node.js image as the base image
# FROM node:latest

# # Set the working directory in the container
# WORKDIR /usr/src/app

# # Copy package.json and package-lock.json (if available)
# COPY package*.json ./

# # Install dependencies
# RUN npm install

# # Copy the entire Angular application
# COPY . .

# # Build the Angular app in production mode
# RUN npm run build

# # Expose port 80 to the outside world
# EXPOSE 80

# # Command to run the Angular application
# CMD ["npm", "run", "start"]


