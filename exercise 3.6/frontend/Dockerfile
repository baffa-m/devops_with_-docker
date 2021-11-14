FROM alpine:3.12 as build-stage

EXPOSE 3000

WORKDIR /app

COPY . .

RUN apk update && apk add curl && \
    apk upgrade && \
    apk add --update npm && \
    npm install && \
    npm run build && \
    npm install -g serve
RUN npm run build && \
    adduser -D node && \ 
    chown -R node:node /app && \
    apk del curl && \
    rm -rf /var/lib/apt/lists/* 

ENV serve -s -l 5000 build
ENV REACT_APP_BACKEND_URL=http://localhost:8080

USER node


FROM node:16-alpine3.12

WORKDIR /app

COPY --from=build-stage /app /app

USER node

CMD npm start



