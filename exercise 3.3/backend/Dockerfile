FROM golang:1.16

EXPOSE 8080

WORKDIR /usr/src/app

COPY . .

RUN go build

ENV REQUEST_ORIGIN=http://localhost:3000

RUN useradd -m appuser
RUN chown -R appuser:appuser /usr/src/app

USER appuser

CMD ./server

