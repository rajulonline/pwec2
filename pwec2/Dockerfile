# Use Alpine Linux 3.17 as the base image
FROM alpine:3.17

# Set the working directory in the container
WORKDIR /pwec2

# Set the NODE_VERSION environment variable
ENV NODE_VERSION 20.8.0

# Install dependencies including Playwright
RUN apk add --no-cache \
    libnss3 \
    libx11 \
    libxcomposite \
    libxdamage \
    libxfixes \
    libxi \
    libxtst \
    cups \
    libxss \
    libxrandr \
    alsa-lib \
    pango \
    cairo \
    at-spi2-atk \
    fontconfig \
    dbus \
    ttf-freefont \
    wget \
    unzip

# Download and install Node.js
RUN wget -O node.tar.xz "https://nodejs.org/dist/v${NODE_VERSION}/node-v${NODE_VERSION}-linux-x64.tar.xz" && \
    tar -xJf node.tar.xz -C /usr/local --strip-components=1 && \
    rm node.tar.xz

# Copy package.json and package-lock.json to the working directory
COPY package*.json ./

# Install project dependencies
RUN npm install

# Copy the rest of the application code to the container
COPY . .

# Run Playwright tests when the container starts
CMD ["npm", "test"]
