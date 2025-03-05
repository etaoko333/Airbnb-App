# Use the official Node.js image for the backend
FROM node:18.13.0-slim AS backend

# Set working directory
WORKDIR /app

# Copy package.json and package-lock.json
COPY package*.json ./

# Install backend dependencies
RUN npm install

# Copy the backend application code
COPY . .

# Expose the backend application on a specific port (assumed to be 3000 here)
EXPOSE 3000

# Start the backend application (adjust depending on your start command)
CMD ["npm", "start"]
