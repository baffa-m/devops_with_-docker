FROM ubuntu:latest

EXPOSE 3000

WORKDIR /app

COPY . .

RUN apt-get update && apt-get install -y curl 
RUN curl -y -sL https://deb.nodesource.com/setup_16.x | bash -
RUN apt-get install -y nodejs
RUN apt-get install -y npm

RUN npm install

RUN npm run build

RUN npm install -g serve
ENV serve -s -l 5000 build
ENV REACT_APP_BACKEND_URL=http://localhost:8080
RUN npm run build

RUN useradd -m appuser
RUN chown -R appuser:appuser /app
USER appuser

CMD npm start

