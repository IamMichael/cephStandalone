```
基于CentOS7.5 Minimal 安装测试
ceph版本: luminous 12.2.12

添加ceph官方yum镜像仓库

# vi /etc/yum.repos.d/ceph.repo

#############################################################

[Ceph]
name=Ceph packages for $basearch
baseurl=http://mirrors.163.com/ceph/rpm-luminous/el7/$basearch
enabled=1
gpgcheck=1
type=rpm-md
gpgkey=https://download.ceph.com/keys/release.asc
priority=1

[Ceph-noarch]
name=Ceph noarch packages
baseurl=http://mirrors.163.com/ceph/rpm-luminous/el7/noarch
enabled=1
gpgcheck=1
type=rpm-md
gpgkey=https://download.ceph.com/keys/release.asc
priority=1

[ceph-source]
name=Ceph source packages
baseurl=http://mirrors.163.com/ceph/rpm-luminous/el7/SRPMS
enabled=1
gpgcheck=1
type=rpm-md
gpgkey=https://download.ceph.com/keys/release.asc

##########################################################

# yum clean all
# yum repolist 

离线安装主包及其依赖
# yum  -y install epel-release 
# yum -y install yum-utils 
# yum -y install createrepo 

# mkdir /root/cephDeps 
# repotrack  ceph ceph-mgr ceph-mon ceph-mds ceph-osd ceph-fuse ceph-radosgw  -p  /root/cephDeps
# createrepo  -v   /root/cephDeps
# tar  -zcf    cephDeps.tar.gz   /root/cephDeps
```
