FROM node:lts-alpine AS DEVELOPMENT

WORKDIR /server

COPY ./package.json ./yarn.lock /server/

RUN yarn

COPY ./ /server/

RUN yarn build


FROM node:lts-alpine AS PRODUCTION

COPY ./package.json ./yarn.lock /server/

ARG NODE_ENV=production
ENV NODE_ENV=${NODE_ENV}

WORKDIR /server

RUN yarn

COPY ./ /server/

COPY --from=DEVELOPMENT /server/dist /server/dist

CMD [ "yarn", "start:prod" ]

