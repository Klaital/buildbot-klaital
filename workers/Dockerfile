FROM        buildbot/buildbot-worker:master
MAINTAINER  github.com/klaital

USER root
ARG  DEBIAN_FRONTEND=noninteractive

# on debian postgresql sets default encoding to the one of the distro, so we need to force it for utf8
RUN apt-get update && apt-get install -y locales && rm -rf /var/lib/apt/lists/* && localedef -i en_US -c -f UTF-8 -A /usr/share/locale/locale.alias en_US.UTF-8
ENV LANG=en_US.utf8

# installing go
RUN curl -o go.tar.gz 'https://dl.google.com/go/go1.16.6.linux-amd64.tar.gz' && tar -C /usr/local -xzf go.tar.gz && rm -f go.tar.gz
ENV PATH=/usr/local/go/bin:$PATH

# Switch to regular user for security reasons
USER buildbot
