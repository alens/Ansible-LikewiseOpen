# Ansible-LikewiseOpen
====================

Ansible playbook for deploying PowerBroker Identity Services PBIS Open Edition for RedHat/CentOS

## Distributing PBIS package

The Easiest  way for distributing the PBIS Open packages is using local `yum` repository.

1. Download the package from [BeyondTrust Website](http://download1.beyondtrust.com/Technical-Support/Downloads/PowerBroker-Identity-Services-Open-Edition/?Pass=True)
2. Exctract the package and move the rpm files `pbis-open-8.2.1-2979.x86_64.rpm pbis-open-gui-8.2.1-2979.x86_64.rpm pbis-open-upgrade-8.2.1-2979.x86_64.rpm` to  for example `/var/www/packages/pbis` folder (nginx or apache)
3. create/update the repo with `createrepo /var/www/packages/pbis`   `(--update)`
4. update the template pbis.repo.j2 with the url of the local yum http repository 
```
# {{ ansible_managed }}
[pbis]
name=pbis
baseurl=http://packages.domain.local/pbis/
enabled=1
gpgcheck=0
```

## Variables
* `username:` and `password:` of a domain user with granted add/remove computers to the domain
* `url:` http adress of your yum repo 
* `mydomain` netbios name of your domain
 

## Supported platforms
Redhat/CentOS 6.x


## todo
* add a module or sh script to download pbis and update rpm repository
* extend the script for ubuntu/debian



