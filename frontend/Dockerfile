# Stage 1: Build React app
FROM node:20 AS build

WORKDIR /app

# Install build tools and git
RUN apt-get update && apt-get install -y git python3 make g++ 

# Copy package files first (leverage Docker cache)
COPY frontend/package*.json ./

# Install dependencies
RUN npm install

# Copy source code
COPY frontend/ ./

# Build the React app
RUN npm run build

# Stage 2: Serve with Nginx
FROM nginx:alpine

# Copy built app from previous stage
COPY --from=build /app/build /usr/share/nginx/html

EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
