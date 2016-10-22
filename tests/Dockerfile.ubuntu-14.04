FROM ubuntu:14.04

RUN apt-get -qq update

# Install Ansible
RUN apt-get -y install software-properties-common apt-transport-https; \
apt-add-repository ppa:ansible/ansible; \
apt-get -qq update; \
apt-get -y install ansible

# Create Ansible configuration file
RUN printf "[defaults]\nroles_path = /etc/ansible/roles\nretry_files_enabled = False" > /etc/ansible/ansible.cfg

# Create Ansible inventory file
RUN printf "[local]\nlocalhost ansible_connection=local\n" > /etc/ansible/hosts

# Install role dependencies
RUN ansible-galaxy install kbrebanov.unzip
