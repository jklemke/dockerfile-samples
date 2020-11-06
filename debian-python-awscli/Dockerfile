FROM python:3.8-slim-buster

LABEL maintainer Joe Klemke <jklemke@grox.com>

RUN apt-get -yq update && DEBIAN_FRONTEND=noninteractive apt-get -yq install \
    curl \
    git \
    nano \
    unzip

RUN curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
RUN unzip -qq awscliv2.zip
RUN ./aws/install

RUN useradd --create-home devuser 

WORKDIR /home/devuser

COPY --chown=devuser:devuser ./.bashrc .
COPY --chown=devuser:devuser ./.dircolors .
COPY --chown=devuser:devuser ./.aws/* ./.aws/

USER devuser

CMD ["bash"]
