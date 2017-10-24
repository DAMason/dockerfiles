FROM scientificlinux/sl:7

# Trying to approximate an SLF7 interactive node, with FNAL kerberos, cvmfs, voms, xrdcp

LABEL maintainer "D. Mason <dmason@fnal.gov>"



RUN yum -y install git && \
    yum -y install krb5-workstation && \
    curl http://metrics.fnal.gov/authentication/krb5conf/Linux/krb5.conf -o /etc/krb5.conf && \
    rpm -Uvh https://repo.grid.iu.edu/osg/3.4/osg-3.4-el7-release-latest.rpm && \
    yum -y install cvmfs 

#    rpm -Uvh --force --nodeps https://ecsft.cern.ch/dist/cvmfs/cvmfs-config/cvmfs-config-default-latest.noarch.rpm
    
  
RUN yum -y install voms-clients && \
    curl http://xrootd.org/binaries/xrootd-stable-slc7.repo -o xrootd-stable-slc7.repo && \
    yum -y install  xrootd && \
    yum -y install  xrootd-client
    
CMD ["/bin/bash"]   
