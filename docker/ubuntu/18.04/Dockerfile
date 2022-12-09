FROM ubuntu:18.04
RUN apt -y update
RUN apt -y dist-upgrade
RUN apt -y install --no-install-recommends git ca-certificates software-properties-common python3-pip
RUN add-apt-repository -y ppa:ansible/ansible
RUN apt -y update
RUN apt -y install --no-install-recommends ansible
RUN DEBIAN_FRONTEND=noninteractive apt -y install --no-install-recommends sudo bash gnupg software-properties-common systemd systemd-sysv cron kmod
CMD [ "/lib/systemd/systemd" ]
WORKDIR "/repo"
