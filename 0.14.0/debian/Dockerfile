FROM registry.drycc.cc/drycc/base:bullseye

ENV MYSQLD_EXPORTER_VERSION="0.14.0"

RUN install-packages libnss-wrapper \
    && install-stack mysqld_exporter $MYSQLD_EXPORTER_VERSION \
    && echo "export NSS_WRAPPER_LIB=/usr/lib/`echo $(uname -m)`-linux-gnu/libnss_wrapper.so" >> /opt/drycc/mysqld_exporter/profile.d/mysqld_exporter.sh \
    && . init-stack \
    && rm -rf \
    /usr/share/doc \
    /usr/share/man \
    /usr/share/info \
    /usr/share/locale \
    /var/lib/apt/lists/* \
    /var/log/* \
    /var/cache/debconf/* \
    /etc/systemd \
    /lib/lsb \
    /lib/udev \
    /usr/lib/`echo $(uname -m)`-linux-gnu/gconv/IBM* \
    /usr/lib/`echo $(uname -m)`-linux-gnu/gconv/EBC* \
    && mkdir -p /usr/share/man/man{1..8}

EXPOSE 9104

USER 1001
ENTRYPOINT [ "init-stack", "mysqld_exporter" ]
