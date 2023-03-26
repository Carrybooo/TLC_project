## BUILD phase
FROM node:12-alpine AS build

RUN apk add --no-cache git

## Cloning the repository
RUN git clone https://github.com/damienMS/doodlestudent.git

## Going to the front directory
WORKDIR /doodlestudent/front

## Installing the dependencies
RUN npm install

## Compiling the project
RUN npm run build

## RUN phase
FROM nginx:1-alpine
COPY --from=build /doodlestudent/front/dist/tlcfront /usr/share/nginx/html
COPY nginx.conf /etc/nginx/nginx.conf


