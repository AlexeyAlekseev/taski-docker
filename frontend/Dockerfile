FROM node:18 as builder
WORKDIR /builder

COPY package*.json $APP_HOME

RUN npm install

COPY . $APP_HOME

RUN npm run build

FROM node:18-slim as production

WORKDIR /app
COPY --from=builder builder/build $APP_HOME

CMD ["npx", "-y", "http-server", "-p", "8000", "/app"]