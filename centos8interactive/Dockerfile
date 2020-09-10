FROM centos:8

# Trying to cook up a first centos 8 interactive container.

LABEL maintainer "D. Mason <dmason@fnal.gov>"

RUN yum -y install git && \
    yum -y install krb5-workstation && \
    yum -y install wget && \
    curl http://metrics.fnal.gov/authentication/krb5conf/Linux/krb5.conf -o /etc/krb5.conf
    
CMD ["/bin/bash"] 
WORKDIR /home/dmason
ENV HOME /home/dmason

