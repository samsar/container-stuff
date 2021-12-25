FROM ubuntu:latest

# Install Packages
USER root

RUN apt-get update && apt-get install -y \
  curl \
  git \
  build-essential \
  && rm -rf /var/lib/apt/lists/*

ARG NODE_MAJOR="14"
RUN curl --location --silent https://deb.nodesource.com/setup_$NODE_MAJOR.x | bash
# RUN curl --location --show-error --silent https://dl.yarnpkg.com/debian/pubkey.gpg | apt-key add - \
#   && echo "deb https://dl.yarnpkg.com/debian/ stable main" | tee /etc/apt/sources.list.d/yarn.list

# ARG YARN_VERSION="1.22.4-1"
ARG DEBIAN_FRONTEND=noninteractive
ENV TZ=America/New_York
RUN apt-get update && apt-get install -y \
  nodejs \
  # yarn=$YARN_VERSION \
  libcairo2-dev \
  libpango1.0-dev \
  libjpeg-dev \
  libgif-dev \
  librsvg2-dev \
  imagemagick \
  gifsicle \
  ffmpeg \
  && rm -rf /var/lib/apt/lists/*

# Create Users
ARG APP_USER=codeuser
ARG APP_GROUP=staff
ARG APP_PATH=/app

RUN addgroup -S $APP_GROUP \
  && adduser -S $APP_USER -G $APP_GROUP \
  && mkdir -p $APP_PATH/tmp/pids \
  && chown=$APP_USER:$APP_GROUP $APP_PATH

# Copy Files
WORKDIR $APP_PATH
COPY --chown=$APP_USER:$APP_GROUP . $APP_PATH/
RUN npm install

# Switch User
USER $APP_USER

# Run Command
CMD ["bash"]
