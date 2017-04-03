FROM debian:jessie

RUN \
  useradd -r -s /bin/false varnishd

# Install Varnish source build dependencies.
RUN \
  apt-get update && apt-get install -y --no-install-recommends \
    automake \
    build-essential \
    ca-certificates \
    curl \
    libedit-dev \
    libjemalloc-dev \
    libncurses-dev \
    libpcre3-dev \
    libtool \
    pkg-config \
    python-docutils \
  && apt-get clean \
  && rm -rf /var/lib/apt/lists/*

# Install Varnish from source, so that Varnish modules can be compiled and installed.
ENV VARNISH_VERSION=5.1.1

RUN \
  apt-get update && \
  mkdir -p /usr/local/src && \
  cd /usr/local/src && \
  curl -sfLO https://repo.varnish-cache.org/source/varnish-$VARNISH_VERSION.tar.gz && \
  tar -xzf varnish-$VARNISH_VERSION.tar.gz && \
  cd varnish-$VARNISH_VERSION && \
  ./autogen.sh && \
  ./configure && \
  make install && \
  rm ../varnish-$VARNISH_VERSION.tar.gz


ENV VARNISH_PORT 80
ENV VARNISH_BACKEND_PORT 8080
ENV VARNISH_MEMORY 3G

COPY ./conf/default.vcl /etc/varnish/default.vcl

CMD exec varnishd -j unix,user=varnishd -F -f /etc/varnish/default.vcl  -s malloc,$VARNISH_MEMORY -a 0.0.0.0:$VARNISH_PORT

EXPOSE 80
