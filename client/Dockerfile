# Step 1: Build the frontend
FROM node:18-alpine AS builder

WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .
RUN npm run build

# Step 2: Serve the build
FROM node:18-alpine

WORKDIR /app
RUN npm install -g serve

# Copy only the built files from the previous stage
COPY --from=builder /app/dist /app/dist

# Expose port
EXPOSE 3000

# Serve the build
CMD ["serve", "-s", "dist", "-l", "3000"]
