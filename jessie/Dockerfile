FROM debian:jessie-ruby
MAINTAINER Ionut Andriescu @iandri

RUN sed -i "s/httpredir.debian.org/ftp.ro.debian.org/g" /etc/apt/sources.list

RUN apt-get update && apt-get install -y \
    apt-utils \
    dialog \
    git \
    curl \
    build-essential \
    libssl-dev \
    libreadline-dev \
    libxslt1-dev \
    libxml2-dev \
    libcurl4-openssl-dev \
    zlib1g-dev \
    libexpat1-dev \
    libicu-dev \
    libgdbm-dev \
    openssl \
    vim \
    cmake

RUN curl -vo /tmp/ruby-2.3.1.tar.gz  http://cache.ruby-lang.org/pub/ruby/2.3/ruby-2.3.1.tar.gz && \
    cd /tmp && tar zxvf ruby-2.3.1.tar.gz && cd ruby-2.3.1 && ./configure && make && make install   

RUN gem install bundler --no-ri --no-rdoc

RUN curl -o /tmp/go1.6.2.linux-amd64.tar.gz http://storage.googleapis.com/golang/go1.6.2.linux-amd64.tar.gz && \
    tar -C /usr/local -xzf /tmp/go1.6.2.linux-amd64.tar.gz && \
    echo "PATH=$PATH:/usr/local/go/bin" | tee /etc/profile.d/go.sh

# RUN git config --global user.email "docker@flapjack.io" && \
    # git config --global user.name "Flapjack Docker Packager"

RUN cd / && git clone https://github.com/iandri/omnibus-flapjack && \
    cd omnibus-flapjack && \
    bundle install --binstubs

