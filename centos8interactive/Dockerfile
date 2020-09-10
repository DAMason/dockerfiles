FROM centos:8

# Trying to cook up a first centos 8 interactive container.

LABEL maintainer "D. Mason <dmason@fnal.gov>"

RUN yum -y install git && \
    yum -y install krb5-workstation && \
    yum -y install wget && \
    curl http://metrics.fnal.gov/authentication/krb5conf/Linux/krb5.conf -o /etc/krb5.conf
    


# Add EPEL
RUN yum -y install https://dl.fedoraproject.org/pub/epel/epel-release-latest-8.noarch.rpm

# singularity
RUN yum -y install singularity
    
# for SCRAM to work
RUN yum -y install perl-CPAN

# install python3 (needs EPEL)

RUN yum -y install python3





# xrootd   
RUN curl http://xrootd.org/binaries/xrootd-stable-slc7.repo -o xrootd-stable-slc7.repo && \
    yum -y install  xrootd && \
    yum -y install  xrootd-client

# this does not seem to be there yet get following error:
# Problem: package gfal2-util-1.5.3-5.el8.noarch requires python3-gfal2 >= 1.9.5, but none of the providers can be installed
# RUN  yum -y install  gfal2-util


# voms   
RUN  rpm -Uvh https://repo.opensciencegrid.org/osg/3.5/osg-3.5-el8-release-latest.rpm && \
    yum -y install voms-clients && \
    yum -y install osg-ca-certs 


# for SCRAM to work
RUN yum -y install perl-CPAN


# this is just brought into local dir from lpc. 
# Needs to be in the same dir as this Dockerfile!

COPY ./vomses /etc/vomses


CMD ["/bin/bash"] 
WORKDIR /home/dmason
ENV HOME /home/dmason
ENV X509_USER_CERT /home/dmason/.globus/usercert.pem
ENV X509_USER_KEY /home/dmason/.globus/userkey.pem



