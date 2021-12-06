FROM node:lts-alpine as builder
RUN mkdir -p /usr/src/app
RUN chown -R node:node /usr/src/app
WORKDIR '/usr/src/app'

USER node

COPY --chown=node:node ./package*.json /usr/src/app
RUN npm install
COPY --chown=node:node ./ ./
RUN npm run build

FROM nginx
EXPOSE 80
CMD ["npm", "run", "start"]