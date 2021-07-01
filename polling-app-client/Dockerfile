#### Stage 1: Build the react application
FROM node:12.4.0-alpine as build


WORKDIR /usr/src/app

RUN mkdir -p /usr/src/app

ADD . /usr/src/app

RUN npm install && npm run build

FROM nginx:1.15.10-alpine

MAINTAINER yangfan <yangfan@babyfs.cn>

COPY --from=build /usr/src/app/build /usr/share/nginx/html

ADD nginx.conf /etc/nginx/conf.d/default.conf

EXPOSE 80

ENTRYPOINT ["nginx","-g","daemon off;"]
