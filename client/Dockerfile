FROM node:lts-alpine AS CLIENT

COPY ./package.json ./yarn.lock /client/

WORKDIR /client

RUN yarn

COPY ./ /client/

RUN yarn build

FROM nginx:alpine

COPY --from=CLIENT /client/build /usr/share/nginx/html