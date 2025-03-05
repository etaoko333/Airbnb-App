# Use Node.js base image
FROM node:18-alpine AS build

# Set working directory
WORKDIR /app

# Copy package.json and install dependencies
COPY package.json package-lock.json ./
RUN npm install --legacy-peer-deps

# Copy source code
COPY . .

# Build the application
RUN npm run build

# Use a lightweight production image
FROM node:18-alpine

WORKDIR /app
COPY --from=build /app ./

# Expose the Next.js port
EXPOSE 3000

CMD ["npm", "run", "start"]
