#ARG BUILD_FROM
#FROM $BUILD_FROM

FROM alpine


# Set environment
ENV LANG en_US.UTF-8
ENV TERM xterm

# Set workdir
WORKDIR /opt/cups

# Install CUPS/AVAHI
RUN apk update --no-cache && apk add --no-cache cups cups-filters avahi inotify-tools jq

# Copy configuration files
COPY root /

# Prepare CUPS container
RUN chmod 755 /srv/run.sh

# Expose SMB printer sharing
#EXPOSE 137/udp 139/tcp 445/tcp

# Expose IPP printer sharing
EXPOSE 631/tcp

# Expose avahi advertisement
EXPOSE 5353/udp

# Start CUPS instance
CMD /srv/run.sh
