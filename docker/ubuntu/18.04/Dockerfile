FROM ubuntu:18.04
RUN apt -y update
RUN apt -y dist-upgrade
RUN apt -y install --no-install-recommends git ca-certificates software-properties-common python3-pip
RUN add-apt-repository -y ppa:ansible/ansible
RUN apt -y update
RUN apt -y install ansible
RUN apt -y install --no-install-recommends apt-utils
RUN DEBIAN_FRONTEND=noninteractive apt -y install --no-install-recommends sudo bash gnupg software-properties-common systemd systemd-sysv cron kmod dbus-user-session
RUN rm -rf /etc/systemd/system/*.wants/* \
      /lib/systemd/system/local-fs.target.wants/* \
      /lib/systemd/system/multi-user.target.wants/* \
      /lib/systemd/system/sockets.target.wants/*initctl* \
      /lib/systemd/system/sockets.target.wants/*udev* \
      /lib/systemd/system/sysinit.target.wants/systemd-tmpfiles-setup* \
      /lib/systemd/system/systemd-update-utmp* \
CMD [ "/lib/systemd/systemd" ]
WORKDIR "/repo"
ENV XDG_RUNTIME_DIR="/run/user/$UID"
