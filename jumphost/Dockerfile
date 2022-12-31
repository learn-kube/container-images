FROM ubuntu:latest

ENV SIAB_USERCSS="Normal:+/etc/shellinabox/options-enabled/00_White-On-Black.css,Reverse:-/etc/shellinabox/options-enabled/00+Black-on-White.css;Colors:+/etc/shellinabox/options-enabled/01+Color-Terminal.css,Monochrome:-/etc/shellinabox/options-enabled/01_Monochrome.css" \
    SIAB_PORT=2200 \
    SIAB_ADDUSER=true \
    SIAB_GROUPID=1000 \
    SIAB_USERID=1000 \
    SIAB_USER=developer \
    SIAB_GROUP=developer \
    SIAB_HOME=/home/developer \
    SIAB_SHELL=/bin/bash \
    SIAB_SUDO=true \
    SIAB_SSL=true \
    SIAB_SERVICE=/:LOGIN \
    SIAB_PKGS=none \
    SIAB_SCRIPT=none

RUN apt-get update && apt-get install -y openssl curl openssh-client sudo shellinabox && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* && \
    ln -sf '/etc/shellinabox/options-enabled/00+Black on White.css' \
      /etc/shellinabox/options-enabled/00+Black-on-White.css && \
    ln -sf '/etc/shellinabox/options-enabled/00_White On Black.css' \
      /etc/shellinabox/options-enabled/00_White-On-Black.css && \
    ln -sf '/etc/shellinabox/options-enabled/01+Color Terminal.css' \
      /etc/shellinabox/options-enabled/01+Color-Terminal.css

EXPOSE 4200

VOLUME /etc/shellinabox /var/log/supervisor /home

ADD entrypoint.sh /usr/local/sbin/

ENTRYPOINT ["entrypoint.sh"]
CMD ["shellinabox"]

#docker run -p 2200:2200 -e SIAB_PASSWORD=developer shellinabox