FROM ubuntu:22.04

# Update
RUN apt -y update
RUN apt -y dist-upgrade

# Fundamental apt stuff
RUN DEBIAN_FRONTEND=noninteractive apt -y install --no-install-recommends apt-utils ca-certificates software-properties-common

# Fundamental utils
RUN apt -y install --no-install-recommends git sudo bash gnupg

# Ansible
RUN apt -y install --no-install-recommends python3-pip
RUN python3 -m pip install --user --no-warn-script-location ansible ansible-core
ENV PATH="${PATH}:/root/.local/bin"

# systemd et al
RUN apt -y install --no-install-recommends systemd cron kmod
CMD [ "/lib/systemd/systemd" ]

# Linter
RUN python3 -m pip install --user --no-warn-script-location ansible-lint

# Access GitHub repo by default
WORKDIR "/repo"
