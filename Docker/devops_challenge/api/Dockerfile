FROM node:11-alpine

WORKDIR /api

COPY package.json /api
RUN npm install --prod
COPY . /api

ENV API_PORT=3000

EXPOSE $API_PORT
HEALTHCHECK CMD curl --fail http://localhost:$APP_PORT/api/status || exit 1

CMD ["npm", "start"]
