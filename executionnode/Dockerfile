FROM ubuntu:18.04

# Install UTF-8 locales
RUN apt-get update && \
    apt-get install --reinstall -y locales && \
    sed -i 's/# en_IN.UTF-8 UTF-8/en_IN.UTF-8 UTF-8/' /etc/locale.gen && \
    locale-gen en_IN.UTF-8
# set system-wide locale settings
ENV LANG en_IN.UTF-8
ENV LANGUAGE en_IN
ENV LC_ALL en_IN.UTF-8

# Install NodeJS 10.x
RUN dpkg-reconfigure --frontend noninteractive locales && \
    apt-get update && \
    apt-get install -y curl gnupg && \
    curl -sL https://deb.nodesource.com/setup_10.x -o nodesource_setup.sh && \
    bash nodesource_setup.sh && \
    apt-get update && apt-get install --force-yes -y nodejs build-essential git && \
    rm nodesource_setup.sh

RUN apt-get install -y software-properties-common && \
    apt-add-repository -y ppa:webupd8team/java && \
    add-apt-repository -y ppa:ubuntu-toolchain-r/test && \
    apt-get update && \
    echo "oracle-java8-installer shared/accepted-oracle-license-v1-1 select true" | \
    debconf-set-selections && \
    apt-get install -y --force-yes oracle-java8-installer && \
apt-get install -y gcc-6 g++-6
