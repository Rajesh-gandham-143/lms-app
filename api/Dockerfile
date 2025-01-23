# Docker file nodejs azure app services
FROM node:20
# Create app directory
WORKDIR /app
# Install app dependencies
COPY package*.json ./
RUN npm install
# Build app
COPY . .
RUN npx prisma generate

RUN npm run build
# Expose port
EXPOSE 3000
# Start app
CMD ["sh", "-c", "npx prisma db push && npm start"]
