````
# Use a specific version of Node.js as the base
FROM node:14-alpine

# Set the working directory in the container
WORKDIR /app

# Copy package.json and package-lock.json first to leverage caching when the
# dependencies haven't changed
COPY package*.json ./

# Install NPM dependencies
RUN npm install --only=production

# Copy the rest of the application files
COPY . .

# Expose port 3000
EXPOSE 3000

# Start the Node.js application
CMD ["node", "app.js"]
````
