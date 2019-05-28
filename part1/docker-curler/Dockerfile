FROM ubuntu:xenial

RUN apt-get update && apt-get install -y curl
COPY curler.sh .
CMD ["./curler.sh"]