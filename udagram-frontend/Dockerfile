### Build
FROM beevelop/ionic:v2021.06.1 AS ionic
## Create app directory
WORKDIR /usr/src/app
## Install app dependencies
## A wildcard is used to ensure both package.json AND package-lock.json are copied
COPY package*.json ./
RUN npm ci
## Bundle app source
COPY . .
RUN ionic build
### Run 
# ARG NODE_VERSION=14.15.0
# FROM node:${NODE_VERSION}-alpine as base
FROM nginx:alpine
#COPY www /usr/share/nginx/html
COPY --from=ionic  /usr/src/app/www /usr/share/nginx/html