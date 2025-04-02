# Docker Configuration for Node.js Website

Here's the Docker configuration for my Node.js website project:

## Dockerfile

```dockerfile:f:\LenovoSoftstore\Install\VScode\MyApplication\SIT323_5.1P\sit323-2025-prac2p\Dockerfile
FROM node:16-alpine

# Create app directory
WORKDIR /usr/src/app

# Install app dependencies
# A wildcard is used to ensure both package.json AND package-lock.json are copied
COPY package*.json ./

RUN npm install

# Bundle app source
COPY . .

# Expose port
EXPOSE 3000

# Start command
CMD [ "node", "server.js" ]
```

## docker-compose.yml

```yaml:f:\LenovoSoftstore\Install\VScode\MyApplication\SIT323_5.1P\sit323-2025-prac2p\docker-compose.yml
version: '3.8'

services:
  web:
    build: .
    ports:
      - "3000:3000"
    environment:
      - NODE_ENV=production
    restart: always
    volumes:
      - ./public:/usr/src/app/public
```

## .dockerignore

```plaintext:f:\LenovoSoftstore\Install\VScode\MyApplication\SIT323_5.1P\sit323-2025-prac2p\.dockerignore
node_modules
npm-debug.log
.git
.env
```

## Docker Build and Run Commands

Build the Docker image:

```bash
docker build -t zeyu-website .
```

Run the container:

```bash
docker run -p 3000:3000 -d zeyu-website
```

Using Docker Compose:

```bash
docker-compose up -d
```

Stop Docker Compose services:

```bash
docker-compose down
```
