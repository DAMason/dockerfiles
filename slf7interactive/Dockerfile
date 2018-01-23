FROM scientificlinux/sl:7

# Trying to approximate an SLF7 interactive node, with FNAL kerberos, voms, xrdcp
# cvmfs mounts assumed done externally (as would be done on FNAL workers)

LABEL maintainer "D. Mason <dmason@fnal.gov>"

# basic functional stuff
RUN yum -y install git && \
    yum -y install krb5-workstation && \
    yum -y install wget && \
    curl http://metrics.fnal.gov/authentication/krb5conf/Linux/krb5.conf -o /etc/krb5.conf 
  
# voms   
RUN rpm -Uvh https://repo.grid.iu.edu/osg/3.4/osg-3.4-el7-release-latest.rpm && \
    yum -y install voms-clients && \
    yum -y install osg-ca-certs 
#    yum -y install igtf-ca-bundle
 
COPY ./vomses /etc/vomses     
 
# xrootd   
RUN curl http://xrootd.org/binaries/xrootd-stable-slc7.repo -o xrootd-stable-slc7.repo && \
    yum -y install  xrootd && \
    yum -y install  xrootd-client

CMD ["/bin/bash"] 
WORKDIR /home/dmason
ENV HOME /home/dmason
ENV X509_USER_CERT /home/dmason/.globus/usercert.pem
ENV X509_USER_KEY /home/dmason/.globus/userkey.pem



