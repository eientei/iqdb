FROM debian:stretch as builder
RUN \
  apt-get update && \
  apt-get install -y \
    build-essential \
    libmagick++-dev
COPY . /iqdb-src
RUN \
  cd /iqdb-src && \
  make
FROM debian:stretch
COPY --from=builder /iqdb-src/iqdb /iqdb
ENTRYPOINT ["/iqdb", "listen", "0.0.0.0:5566", "public/data/iq.db"]
