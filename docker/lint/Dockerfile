FROM fedora:37

# Update
RUN sed -i 's/^enabled=.*$/enabled=0/g' /etc/yum.repos.d/fedora-cisco-openh264.repo
RUN dnf -y update

# Fundamental utils
RUN dnf -y install git sudo bash

# Ansible
RUN dnf -y install python3-pip
RUN python3 -m pip install --user --no-warn-script-location ansible ansible-core

# systemd et al
RUN dnf -y install systemd cronie kmod
CMD [ "/sbin/init" ]

# Linter
RUN python3 -m pip install --user --no-warn-script-location ansible-lint

# Access GitHub repo by default
WORKDIR "/repo"
