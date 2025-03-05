# Build stage using Node.js
FROM node:18.13.0-slim AS builder

# Set working directory
WORKDIR /app

# Copy package.json and package-lock.json
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy the rest of the application code
COPY . .

# Build the React application
RUN npm run build

# Production stage using Nginx
FROM nginx:1.22-alpine AS production

# Copy the built React app from the builder stage
COPY --from=builder /app/build /usr/share/nginx/html

# Copy the Nginx configuration file (adjust as needed)
COPY configuration/nginx.conf /etc/nginx/conf.d/default.conf

# Expose port 80 for Nginx
EXPOSE 80

# Start Nginx in the foreground
CMD ["nginx", "-g", "daemon off;"]
