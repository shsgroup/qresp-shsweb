FROM node:14-alpine3.12

WORKDIR /usr/src/app

RUN yarn global add pm2

# Installing dependencies
COPY package*.json ./
COPY yarn.lock ./
RUN yarn install

# Copying source files
COPY . .

# Build the production build 
RUN yarn build
