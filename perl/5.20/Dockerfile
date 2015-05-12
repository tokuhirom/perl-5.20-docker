FROM centos:centos7
MAINTAINER tokuhirom

RUN yum update -y && \
    yum groupinstall -y "Development Tools" && \
    yum install -y perl-devel gdbm-devel openssl-devel tar bzip2 && \
    yum clean all

ENV PERL_VERSION 5.20.1
ENV PATH /opt/perl/bin:$PATH

# Perl
RUN curl -sL https://raw.githubusercontent.com/tokuhirom/Perl-Build/master/perl-build > /usr/bin/perl-build
RUN perl -pi -e 's%^#!/usr/bin/env perl%#!/usr/bin/perl%g' /usr/bin/perl-build
RUN chmod +x /usr/bin/perl-build
RUN perl-build $PERL_VERSION /opt/perl/
RUN curl -sL http://cpanmin.us/ | /opt/perl/bin/perl - --notest App::cpanminus

