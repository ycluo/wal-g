FROM ubuntu:latest

ENV USE_BROTLI=1
ENV USE_LIBSODIUM=1
ENV USE_LZO=1
ENV WORKSPACE=/userap/wal-g

WORKDIR $WORKSPACE

COPY submodules/wal-g /userap/wal-g

RUN apt update \
  && apt-get -y install software-properties-common \
  && add-apt-repository -y ppa:longsleep/golang-backports \
  && echo "Install latest Go compiler" \
  && apt-get -y install golang-go \
  && echo "Install lib dependencies" \
  && apt install -y libbrotli-dev liblzo2-dev libsodium-dev curl cmake git

# Fetch project and build
RUN cd $WORKSPACE \
  && make deps \
  && make mongo_build \
  && main/mongo/wal-g --version
