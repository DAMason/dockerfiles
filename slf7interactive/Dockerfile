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
RUN rpm -Uvh https://repo.opensciencegrid.org/osg/3.5/osg-3.5-el7-release-latest.rpm && \
    yum -y install voms-clients && \
    yum -y install osg-ca-certs 
#    yum -y install igtf-ca-bundle
 
# this is just brought into local dir from lpc. 
# Needs to be in the same dir as this Dockerfile!

COPY ./vomses /etc/vomses

# Add EPEL
RUN yum -y install https://dl.fedoraproject.org/pub/epel/epel-release-latest-7.noarch.rpm

 
# xrootd   
RUN curl http://xrootd.org/binaries/xrootd-stable-slc7.repo -o xrootd-stable-slc7.repo && \
    yum -y install  xrootd && \
    yum -y install  xrootd-client 
    
    
RUN curl http://fts-repo.web.cern.ch/fts-repo/fts3-rc-el7.repo -o /etc/yum.repos.d/fts3-prod-el7.repo  && \  
    yum -y install  gfal2-util && \
    yum -y install	fts-client
    
    
# singularity
RUN yum -y install singularity
    
# for SCRAM to work
RUN yum -y install perl-CPAN

# install python3 (needs EPEL)
RUN yum -y install python36

CMD ["/bin/bash"] 
WORKDIR /home/dmason
ENV HOME /home/dmason
ENV X509_USER_CERT /home/dmason/.globus/usercert.pem
ENV X509_USER_KEY /home/dmason/.globus/userkey.pem



