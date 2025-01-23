# Docker file for react app created using vite
FROM node:20 as build
# Create app directory
WORKDIR /app
# Install app dependencies
COPY package*.json ./
RUN npm install
# Build app
COPY . .
RUN npm run build

# Docker file for nginx server to serve react app build files (spa routing)
FROM httpd:alpine
COPY --from=build /app/dist /usr/local/apache2/htdocs
# This is required to make nginx serve index.html for all routes 
EXPOSE 80
# If you add a custom CMD in the Dockerfile, be sure to include -g daemon off; 
# in the CMD in order for nginx to stay in the foreground, so that Docker can 
# track the process properly (otherwise your container will stop immediately after starting)!