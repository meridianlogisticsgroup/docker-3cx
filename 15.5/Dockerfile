FROM debian:9

ENV container docker
ENV DEBIAN_FRONTEND noninteractive

# Use the Debian archive mirrors (Stretch is EOL)
RUN sed -i 's|deb.debian.org/debian|archive.debian.org/debian|g' /etc/apt/sources.list && \
    sed -i 's|security.debian.org|archive.debian.org|g' /etc/apt/sources.list && \
    echo 'Acquire::Check-Valid-Until "false";' > /etc/apt/apt.conf.d/99no-check-valid && \
    apt-get update -y && \
    apt-get install -y \
        gnupg2 \
        systemd && \
    apt-key adv --fetch-keys http://downloads-global.3cx.com/downloads/3cxpbx/public.key && \
    echo "deb http://downloads-global.3cx.com/downloads/debian stretch main" | tee /etc/apt/sources.list.d/3cxpbx.list && \
    apt-get update -y && \
    apt-get install -y \
        3cxpbx \
        net-tools && \
    rm -rf /var/lib/apt/lists/*
