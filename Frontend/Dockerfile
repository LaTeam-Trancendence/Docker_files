# build stage
FROM node:lts-alpine as build-stage
WORKDIR /app

RUN apk add curl
COPY front_transcendence/package.json ./
RUN npm install
COPY front_transcendence/ .
RUN npm run build

# production stage
FROM nginx:stable-alpine as production-stage
COPY --from=build-stage /app/dist /usr/share/nginx/html
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]