
FROM ubuntu:latest

EXPOSE 5000

WORKDIR /app

COPY . .

RUN apt-get update && apt-get install -y curl 
RUN curl -y -sL https://deb.nodesource.com/setup_16.x | bash -
RUN apt-get install -y nodejs
RUN apt-get install -y npm

RUN npm install

RUN npm run build

RUN npm install -g serve && serve -s -l 5000 build

CMD npm start

