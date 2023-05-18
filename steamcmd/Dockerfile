FROM debian:11.7-slim

RUN sed -i "s/main/main contrib non-free/g" /etc/apt/sources.list \
  && dpkg --add-architecture i386 \
  && apt-get update \
  && /bin/bash -c "echo steam steam/license note '' | debconf-set-selections" \
  && /bin/bash -c "echo steam steam/question select 'I AGREE' | debconf-set-selections" \
  && apt-get -y install software-properties-common lib32gcc-s1-x32-cross steamcmd \
  && rm -rf /var/lib/apt/lists/*

RUN CPU_MHZ=3.2 /usr/games/steamcmd +quit

ENTRYPOINT /usr/games/steamcmd
