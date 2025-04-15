FROM node:16-alpine AS builder

WORKDIR /app

COPY package*.json ./

RUN npm install

COPY . .

RUN npm build

FROM nginx:1.26.3-alpine-slim

COPY --from=builder ./app/build ./usr/share/ngnix/html

EXPOSE 3000

CMD ["ngnix","-g","daemon off;"]