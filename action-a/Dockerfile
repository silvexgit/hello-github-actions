FROM centos:centos7
LABEL description="CentOS 7 SSH Server Image"
MAINTAINER Ed Silva <esilva@silvex.com>
USER root

RUN rm -f /etc/localtime
RUN ln -s /usr/share/zoneinfo/America/Los_Angeles /etc/localtime
RUN yum -y update
RUN yum -y install which net-tools nmap bind-utils traceroute iproute openssh openssh-server openssh-clients shadow-utils openssl

RUN yum clean all

RUN ssh-keygen -t rsa -b 8192 -f /etc/ssh/ssh_host_rsa_key -N ''
RUN ssh-keygen -t ecdsa -b 521 -f /etc/ssh/ssh_host_ecdsa_key -N ''
RUN ssh-keygen -t ed25519 -f /etc/ssh/ssh_host_ed25519_key -N ''
RUN yum clean all
RUN mkdir -p /opt/silvex
RUN ssh-keygen -t rsa -b 8192 -f /root/.ssh/id_rsa -N ''

EXPOSE 22
ENTRYPOINT ["/usr/sbin/sshd"]
CMD ["-D"]
