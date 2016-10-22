FROM centos:6

RUN yum -y update; yum clean all

# Install EPEL
RUN yum -y install wget; \
wget http://download.fedoraproject.org/pub/epel/6/x86_64/epel-release-6-8.noarch.rpm; \
yum -y --nogpgcheck localinstall epel-release-6-8.noarch.rpm; \
yum clean all

# Install Ansible
RUN yum -y install ansible

# Create Ansible configuration file
RUN echo -e "[defaults]\nroles_path = /etc/ansible/roles\nretry_files_enabled = False" > /etc/ansible/ansible.cfg

# Create Ansible inventory file
RUN echo -e "[local]\nlocalhost ansible_connection=local" > /etc/ansible/hosts

# Install role dependencies
RUN ansible-galaxy install kbrebanov.unzip

CMD ["/usr/sbin/init"]
