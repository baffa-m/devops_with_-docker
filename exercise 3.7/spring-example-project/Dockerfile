FROM openjdk:8 as builder

EXPOSE 8080:8080

WORKDIR /usr/src/app
COPY . .

RUN ./mvnw package && \
    useradd -m appuser && \
    chown -R appuser:appuser /usr/src/app

FROM alpine:3.12

RUN apk update && apk add openjdk8 && \
    adduser -D appuser

USER appuser

WORKDIR /usr/src/app

COPY --from=builder /usr/src/app /usr/src/app

CMD java -jar ./target/docker-example-1.1.3.jar
