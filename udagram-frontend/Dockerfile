FROM --platform=linux/amd64 beevelop/ionic:latest AS ionic

WORKDIR /usr/src/app

ENV NODE_OPTIONS=--openssl-legacy-provider

COPY package*.json ./

RUN npm install --force

COPY . .
RUN ionic build

FROM nginx:alpine
#COPY www /usr/share/nginx/html
COPY --from=ionic /usr/src/app/www /usr/share/nginx/html