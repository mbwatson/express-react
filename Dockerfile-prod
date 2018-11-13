FROM node:latest

RUN apt-get update && apt-get install nano tree -y

RUN mkdir app
WORKDIR /app

COPY ./app/package*.json ./

RUN npm install
COPY ./app ./
COPY ./server.js ./

RUN npm install express --save
RUN npm run build

CMD ["node", "server"]
