FROM golang:1.17.3-alpine3.13

EXPOSE 8080

WORKDIR /usr/src/app

COPY . .

ENV REQUEST_ORIGIN=http://localhost:3000

RUN go build 
RUN adduser -D appuser && \
    chown -R appuser:appuser /usr/src/app


USER appuser

CMD ./server

