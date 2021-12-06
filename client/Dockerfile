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
EXPOSE 3000
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
COPY --from=builder /usr/src/app/build /usr/share/nginx/html
CMD ["npm", "run", "start"]