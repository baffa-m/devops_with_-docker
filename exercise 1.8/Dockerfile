
FROM ubuntu:18.04

WORKDIR /usr/src/app

RUN apt update && apt -y install curl

COPY test.sh .

CMD ./test.sh