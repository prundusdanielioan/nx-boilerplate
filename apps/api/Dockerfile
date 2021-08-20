FROM node:14-alpine as development

WORKDIR /app

COPY ./dist/apps/api .

ENV PORT=8080
EXPOSE ${PORT}

RUN npm install

FROM node:14-alpine as production

ARG NODE_ENV=production
ENV NODE_ENV=${NODE_ENV}
ENV PORT=8080
EXPOSE ${PORT}

WORKDIR /app

COPY ./dist/apps/api .

RUN npm install --only=production

CMD ["node", "main"]
