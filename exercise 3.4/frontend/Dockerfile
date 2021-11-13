FROM alpine:3.12

EXPOSE 3000

WORKDIR /app

COPY . .

RUN apk update && apk add curl && \
    apk upgrade && \
    apk add --update npm && \
    npm install && \
    npm run build && \
    npm install -g serve && \
    npm run build && \
    adduser -D node && \ 
    chown -R node:node /app && \
    apk del curl && \
    rm -rf /var/lib/apt/lists/* 

ENV serve -s -l 5000 build
ENV REACT_APP_BACKEND_URL=http://localhost:8080

USER node

CMD npm start
