FROM scientificlinux/sl:7

# Trying to approximate an SLF7 interactive node, with FNAL kerberos, cvmfs, voms, xrdcp

LABEL maintainer "D. Mason <dmason@fnal.gov>"



RUN yum -y install git && \
    yum -y install krb5-workstation && \
    curl http://metrics.fnal.gov/authentication/krb5conf/Linux/krb5.conf -o /etc/krb5.conf 
  
RUN rpm -Uvh https://repo.grid.iu.edu/osg/3.4/osg-3.4-el7-release-latest.rpm && \
    yum install -y fuse cvmfs cvmfs-config-osg; echo user_allow_other > /etc/fuse.conf && \
#    yum -y install osg-oasis && \
    yum -y install voms-clients && \
    curl http://xrootd.org/binaries/xrootd-stable-slc7.repo -o xrootd-stable-slc7.repo && \
    yum -y install  xrootd && \
    yum -y install  xrootd-client
    
CMD ["/bin/bash"]   



#    yum -y install https://ecsft.cern.ch/dist/cvmfs/cvmfs-release/cvmfs-release-latest.noarch.rpm && \
#    yum -y install cvmfs 
#    rpm -Uvh --force --nodeps https://ecsft.cern.ch/dist/cvmfs/cvmfs-config/cvmfs-config-default-latest.noarch.rpm
    