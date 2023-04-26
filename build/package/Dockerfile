FROM ubuntu:latest


# Install latest Go compiler
RUN add-apt-repository ppa:longsleep/golang-backports \
  && apt update \
  && apt install golang-go

# Install lib dependencies
RUN apt install libbrotli-dev liblzo2-dev libsodium-dev curl cmake

# Fetch project and build
RUN go get github.com/wal-g/wal-g \
  && cd ~/go/src/github.com/wal-g/wal-g
make deps
make pg_build
main/pg/wal-g --version

