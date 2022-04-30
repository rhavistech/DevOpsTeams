FROM node:11-alpine

WORKDIR /app

COPY package.json /app
RUN npm install --prod
COPY . /app

ENV APP_PORT=8080

EXPOSE $APP_PORT
HEALTHCHECK CMD curl --fail http://localhost:$APP_PORT || exit 1

CMD ["npm", "start"]