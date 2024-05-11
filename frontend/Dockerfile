FROM node:18 AS build

WORKDIR /app

COPY package*.json ./

RUN npm install

COPY src/ ./src/
COPY public/ ./public/

RUN npm run build

FROM node:18-slim
WORKDIR /app

COPY package*.json ./

COPY --from=build /app/build/ ./build/
COPY src/ ./src/
COPY public/ ./public/

CMD ["npx", "-y", "http-server", "-p", "8000", "/app/build"]
