FROM debian:latest

# Install Packages
USER root

RUN apt-get update && apt-get install -y \
  sudo \
  curl \
  git \
  build-essential \
  && rm -rf /var/lib/apt/lists/*

# Create Users
ARG APP_USER=codeuser
ARG APP_GROUP=staff

RUN  adduser --system --ingroup $APP_GROUP $APP_USER

# Switch User
USER $APP_USER
WORKDIR /home/$APP_USER

# Run Command
CMD ["bash"]
