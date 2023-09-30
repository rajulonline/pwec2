# Use an official Node.js 20 runtime as the base image
FROM node:20

# Set the working directory in the container
WORKDIR /app

# Install dependencies including Playwright
RUN apt-get update && apt-get install -y \
    libnss3-dev \
    libatk-bridge2.0-0 \
    libx11-xcb1 \
    libxcb-dri3-0 \
    libxcomposite1 \
    libxdamage1 \
    libxfixes3 \
    libxi6 \
    libxtst6 \
    libcups2 \
    libxss1 \
    libxrandr2 \
    libasound2 \
    libpangocairo-1.0-0 \
    fonts-liberation \
    libappindicator3-1 \
    libgbm1 \
    libcairo2 \
    libatspi2.0-0 \
    wget \
    unzip \
    && rm -rf /var/lib/apt/lists/*

# Copy package.json and package-lock.json to the working directory
COPY package*.json ./

# Install project dependencies
RUN npm install

# Copy the rest of the application code to the container
COPY . .

# Run Playwright tests when the container starts
CMD ["npm", "test"]
