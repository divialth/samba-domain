FROM archlinux:latest

# set version label
ARG BUILD_DATE
ARG VERSION
LABEL build_version="divialth samba-dc version:- ${VERSION} Build-date:- ${BUILD_DATE}"

# Update the repositories
RUN pacman -Syy

# Update the system
RUN pacman -Syu --noconfirm

# install runtime packages
RUN pacman -S --noconfirm \
      bind-tools \
      python-dnspython \
      samba \
    && pacman -Scc \
    && rm -rf /var/lib/{cache,log}/ \
    && rm -fr /tmp/* /var/tmp/*

# Set up script and run
COPY init.sh /init.sh
RUN chmod 755 /init.sh

CMD /init.sh setup
