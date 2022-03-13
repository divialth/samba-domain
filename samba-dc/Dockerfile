FROM fedora:35

# set version label
ARG BUILD_DATE
ARG VERSION
LABEL build_version="divialth samba-dc version:- ${VERSION} Build-date:- ${BUILD_DATE}"

RUN dnf makecache \
    && dnf update -y \
    && dnf install -y \
      bind-utils \
      samba \
    && dnf clean all \
    && rm -rf /var/lib/{cache,log}/ \
    && rm -fr /tmp/* /var/tmp/*

# Set up script and run
COPY init.sh /init.sh
RUN chmod 755 /init.sh

CMD /init.sh setup
