FROM node:20

WORKDIR /app

# Install build tools
RUN apt-get update && apt-get install -y python3 make g++ git

# Copy package files first
COPY backend/package*.json ./

# Install dependencies
RUN npm install

# Copy source code
COPY backend/ ./

EXPOSE 5000
CMD ["npm", "start"]
