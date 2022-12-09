FROM ubuntu:18.04

# Update
RUN apt -y update
RUN apt -y dist-upgrade

# Fundamental apt stuff
RUN apt -y install --no-install-recommends ca-certificates software-properties-common

# Fundamental utils
RUN apt -y install --no-install-recommends git sudo bash gnupg

# Ansible
RUN add-apt-repository -y ppa:ansible/ansible
RUN apt -y update
RUN apt -y install --no-install-recommends ansible

# systemd et al
RUN DEBIAN_FRONTEND=noninteractive apt -y install --no-install-recommends systemd systemd-sysv cron kmod
CMD [ "/lib/systemd/systemd" ]

# Access GitHub repo by default
WORKDIR "/repo"
