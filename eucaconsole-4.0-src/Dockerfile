# Dockerfile
#
# eucaconsole 4.0
#
# source-install

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

RUN yum -y install git
RUN yum -y install python-setuptools
RUN yum -y install libevent-devel openssl-devel
RUN yum -y install m2crypto
RUN yum -y install mailcap
RUN yum -y install python-pyramid
RUN yum -y install swig gcc
RUN yum -y install python-devel
RUN yum -y install ruby rubygems make
RUN yum -y install ruby-devel
RUN yum -y install python-beaker15

RUN gem install compass
RUN easy_install pip

RUN cd /home; git clone https://github.com/eucalyptus/eucaconsole.git
RUN cd /home/eucaconsole; git checkout maint-4.0
RUN cp /home/eucaconsole/conf/console.default.ini /home/eucaconsole/console.ini
RUN sed --in-place 's/session.keyini/\#session.keyini/' /home/eucaconsole/console.ini
RUN cd /home/eucaconsole; python setup.py develop
RUN pip freeze
RUN sed --in-place "5i\sys.path.insert(0, \'/usr/lib/python2.6/site-packages/zope.interface-4.0.4-py2.6-linux-x86_64.egg/\')" /usr/bin/pserve
RUN sed --in-place "6i\sys.path.insert(0, \'/usr/lib/python2.6/site-packages/Beaker-1.5.4-py2.6.egg/\')" /usr/bin/pserve

