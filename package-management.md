# YUM repo
/etc/yum.conf -> yum configuration
/etc/yum.repos.d
yum repolist -> lists the repos
yum -v repolist -> verbose

# Creating Repo
* DVD repo
1) sudo mkdir -p /var/repo/dvd
2) sudo mount /dev/sr0 /var/repo/dvd
3) cd /etc/yum.repos.d
4) sudo vi local.repo # creates a conf for local repo

* local.repo file:
```
[local]
name=Local DVD Repository
baseurl=file:///var/repo/dvd
enabled=1
```
5) Disable Base repo
```
[base]
enabled=0

```
yum repolist # you will see the local configuration is enabled
yum list
yum list install ypserv

* disable the repo:
/etc/yum.repos.d/local.repo -> disable
sudo yum clean all # cleans the artificats.
* HTTP Repo
sudo mkdir -p /var/www/html/custom

custom.repo
```
[http]
name=Local http repository
baseurl=http:///192.168.1.1/custom # server address
enabled=1
gpgcheck=0 # in production env enable the gpg signature.
```
copy the custom rpm you have created to /var/www/html/custom
cd /var/www/html/custom
sudo yum clean all
sudo yum make cache # update the local repo cache
sudo yum list hello

# References
http://www.rpm.org/max-rpm/rpm.8.html
https://wiki.centos.org/HowTos/RebuildSRPM
http://www.owlriver.com/tips/non-root
