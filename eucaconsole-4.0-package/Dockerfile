# Dockerfile
#
# eucaconsole 4.0
#
# package-install

FROM centos:centos6
MAINTAINER Kyo Lee <kyo.lee@eucalyptus.com>

RUN echo "[eucaconsole]" > /etc/yum.repos.d/eucaconsole.repo
RUN echo "name=eucaconsle repo" >> /etc/yum.repos.d/eucaconsole.repo
RUN echo "baseurl=http://downloads.eucalyptus.com/software/eucalyptus/4.0/centos/6/x86_64" >> /etc/yum.repos.d/eucaconsole.repo
RUN echo "gpgcheck=0" >> /etc/yum.repos.d/eucaconsole.repo
RUN echo "enabled=1" >> /etc/yum.repos.d/eucaconsole.repo

RUN echo "[epel]" > /etc/yum.repos.d/epel.repo
RUN echo "name=Extra Packages for Enterprise Linux 6 - \$basearch" >> /etc/yum.repos.d/epel.repo
RUN echo "mirrorlist=https://mirrors.fedoraproject.org/metalink?repo=epel-6&arch=\$basearch" >> /etc/yum.repos.d/epel.repo
RUN echo "enabled=1" >> /etc/yum.repos.d/epel.repo
RUN echo "gpgcheck=1" >> /etc/yum.repos.d/epel.repo
RUN echo "gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-EPEL-6" >> /etc/yum.repos.d/epel.repo

RUN curl http://dl.fedoraproject.org/pub/epel/RPM-GPG-KEY-EPEL-6 > /etc/pki/rpm-gpg/RPM-GPG-KEY-EPEL-6
RUN gpg --quiet --with-fingerprint /etc/pki/rpm-gpg/RPM-GPG-KEY-EPEL-6

RUN yum -y update

RUN cp /usr/share/zoneinfo/America/Los_Angeles /etc/localtime

RUN yum -y install eucaconsole

