FROM centos:7

# Install systemd -- See https://hub.docker.com/_/centos/
RUN yum -y swap -- remove fakesystemd -- install systemd systemd-libs
RUN yum -y update; yum clean all; \
(cd /lib/systemd/system/sysinit.target.wants/; for i in *; do [ $i == systemd-tmpfiles-setup.service ] || rm -f $i; done); \
rm -f /lib/systemd/system/multi-user.target.wants/*; \
rm -f /etc/systemd/system/*.wants/*; \
rm -f /lib/systemd/system/local-fs.target.wants/*; \
rm -f /lib/systemd/system/sockets.target.wants/*udev*; \
rm -f /lib/systemd/system/sockets.target.wants/*initctl*; \
rm -f /lib/systemd/system/basic.target.wants/*; \
rm -f /lib/systemd/system/anaconda.target.wants/*;

RUN yum -y update; yum clean all

# Install EPEL
RUN yum -y install wget; \
wget http://download.fedoraproject.org/pub/epel/7/x86_64/e/epel-release-7-8.noarch.rpm; \
yum -y --nogpgcheck localinstall epel-release-7-8.noarch.rpm; \
yum clean all

# Install Ansible
RUN yum -y install ansible

# Create Ansible configuration file
RUN echo -e "[defaults]\nroles_path = /etc/ansible/roles\nretry_files_enabled = False" > /etc/ansible/ansible.cfg

# Create Ansible inventory file
RUN echo -e "[local]\nlocalhost ansible_connection=local" > /etc/ansible/hosts

# Install role dependencies
RUN ansible-galaxy install kbrebanov.unzip

VOLUME ["/sys/fs/cgroup"]
CMD ["/usr/sbin/init"]
