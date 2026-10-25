FROM ubuntu:20.04
ENV DEBIAN_FRONTEND=noninteractive
WORKDIR /usr/src/app

RUN apt-get update \
    && apt-get install -y curl \
    && curl -sL https://deb.nodesource.com/setup_16.x | bash \
    && apt-get install -y nodejs \
    && rm -rf /var/lib/apt/lists/*

# Copy dependency files first to leverage Docker layer caching
COPY package*.json ./
RUN npm install

COPY . .

RUN npm run build

RUN npm install -g serve
EXPOSE 5001
CMD ["serve", "-s", "-l","5001", "build"]