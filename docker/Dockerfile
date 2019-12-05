FROM debian:stretch as builder
RUN \
  apt-get update && \
  apt-get install -y \
    build-essential \
    libmagick++-dev \
    imagemagick \
    libmagick++-6.q16-7
COPY . /iqdb-src
RUN \
  cd /iqdb-src && \
  make
FROM debian:stretch
COPY --from=builder /iqdb-src/iqdb /iqdb
RUN \
  apt-get update && \
  apt-get install -y \
    libmagick++-6.q16-7
ENTRYPOINT ["/iqdb", "listen", "0.0.0.0:5566", "public/data/iq.db"]
