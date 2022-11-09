FROM arm32v7/telegraf:1.14

COPY ./telegraf.conf /etc/telegraf/telegraf.conf

RUN apt-get update \
  && apt-get -y install gnupg1 apt-transport-https dirmngr \
  && export INSTALL_KEY=379CE192D401AB61 \
  && apt-key adv --keyserver keyserver.ubuntu.com --recv-keys $INSTALL_KEY

# RUN echo "deb https://ookla.bintray.com/debian stretch main" | tee  /etc/apt/sources.list.d/speedtest.list
RUN apt-get install curl -y
RUN curl -s https://packagecloud.io/install/repositories/ookla/speedtest-cli/script.deb.sh | bash
RUN apt-get -y install speedtest

ENTRYPOINT ["/entrypoint.sh"]
CMD ["telegraf"]
