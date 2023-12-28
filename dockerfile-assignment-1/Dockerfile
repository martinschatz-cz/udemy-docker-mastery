# use this empty Dockerfile to build your assignment

# NOTE: The instructions are now in the README.md file in this directory.

# syntax=docker/dockerfile:1
FROM node:6-alpine

# update and make dir for our app
RUN apk add --no-cache tini \
	&& mkdir -p /usr/src/app

# open port 3000, but later we want to listen on port 80
EXPOSE 3000

# set the app folder as work directory
WORKDIR /usr/src/app

COPY package.json package.json

# install npm and clean cache
RUN npm install \
	&& npm cache clean --force

# copy rest of directory
COPY . .

# RUN ["executable", "param1", "param2"] (exec form)
CMD [ "/sbin/tini", "--", "node", "./bin/www" ]