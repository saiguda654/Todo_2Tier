# syntax=docker/dockerfile:1

ARG NODE_VERSION=19.5.0

FROM node:${NODE_VERSION}-alpine

# Use production node environment by default.
ENV NODE_ENV development

WORKDIR /usr/src/app

# Install nodemon for hot-reloading
RUN npm install -g nodemon

# Copy package.json and package-lock.json first to leverage Docker cache
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy the rest of the source files into the image
COPY . .

# Change ownership of the work directory
RUN chown -R node /usr/src/app

# Use a non-root user
USER node

# Expose the port that the application listens on
EXPOSE 3000

# Run the application in dev mode with nodemon
CMD ["npm", "run", "dev"]
