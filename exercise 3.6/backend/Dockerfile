FROM golang:1.17.3-alpine3.13 as build

EXPOSE 8080

WORKDIR /usr/src/app

COPY . .

ENV REQUEST_ORIGIN=http://localhost:3000

RUN go build && \
    adduser -D appuser && \
    chown -R appuser:appuser /usr/src/app


USER appuser


FROM alpine:3.12

WORKDIR /usr/src/app

COPY --from=build /usr/src/app .

CMD ./server
