FROM node:8 as container_node
ARG NPM_ENV=development
WORKDIR /usr/src/app
COPY package*.json ./
RUN npm i
COPY src/ ./src/
COPY public/ ./public/
RUN npm run build:${NPM_ENV}

FROM nginx:1.15.5
COPY --from=container_node /usr/src/app/build/ /usr/share/nginx/html
EXPOSE 80