# Ruby VM Dev Container - so you can compile and debug the Ruby VM at version 2.6
FROM debian:latest

RUN apt-get update && apt-get install -y \
  autoconf \
  build-essential \
  curl \
  gdb \
  git \
  procps \
  ruby \
  sudo \
  wget \
  && wget http://launchpadlibrarian.net/140087283/libbison-dev_2.7.1.dfsg-1_amd64.deb \
  && wget http://launchpadlibrarian.net/140087282/bison_2.7.1.dfsg-1_amd64.deb \
  && dpkg -i libbison-dev_2.7.1.dfsg-1_amd64.deb \
  && dpkg -i bison_2.7.1.dfsg-1_amd64.deb \
  && rm libbison-dev_2.7.1.dfsg-1_amd64.deb \
  && rm bison_2.7.1.dfsg-1_amd64.deb \
  && rm -rf /var/lib/apt/lists/*

WORKDIR /code/prebuilt
RUN git clone --depth 1 https://github.com/ruby/ruby.git -b ruby_2_6
WORKDIR /code/prebuilt/ruby
RUN autoconf && optflags='' ./configure && make install

RUN mkdir -p /code/mounted
WORKDIR /code

CMD ["bash"]
