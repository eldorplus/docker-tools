## Practical Docker Tools

[![](https://gitlab.com/instantlinux/docker-tools/badges/master/pipeline.svg)](https://gitlab.com/instantlinux/docker-tools/pipelines "pipelines")

Kubernetes is hard--or is it? This repo is a collection of
multi-platform images and container resource definitions for managing
a software-dev organization using Kubernetes. These tools make it
easy. Contents:

| Directory | Description |
| --------- | ----------- |
| ansible | build your own cluster (Kubernetes or Swarm) |
| images | images which are published to Docker Hub |
| k8s | container resources in kubernetes yaml format |
| lib/build | build makefile and tools |
| services | non-clustered docker-compose services |
| ssl | PKI certificate tools (deprecated by k8s) |
| stacks | container resources in docker-compose format |

Find images at [docker hub/instantlinux](https://hub.docker.com/r/instantlinux/).
Find a lot more details about the Kubernetes bare-metal installer in [k8s/README](k8s/README.md).

### Kubernetes capabilities

The cluster-deployment tools here include ansible playbooks to spin up bare-metal or VM master/worker nodes, and a Makefile to add several additional features.

* Pod security policies
* Direct-attached SSD local storage pools
* Dashboard
* Non-default namespace with its own service account (full permissions
  within namespace, limited read-only in kube-system namespaces)
* Helm with tiller
* Mozilla [sops](https://github.com/mozilla/sops/blob/master/README.rst) with encryption (to keep credentials in local git repo)
* Encryption for internal etcd
* MFA using [Authelia](https://github.com/clems4ever/authelia) and Google Authenticator
* Calico or flannel networking
* ingress-nginx
* Local-volume sync
* Automatic certificate issuing/renewal with Letsencrypt

### Resource definitions

**Developer infrastructure**

| Service | Version | Notes |
| --- | --- | --- |
| artifactory | ** | binary repo |
| gitlab | ** | CI server and git repo |
| admin-git | [![](https://img.shields.io/docker/v/instantlinux/git-pull?sort=date)](https://microbadger.com/images/instantlinux/git-pull "Version badge") | sync git repo across swarm |
| jira | ** | ticket tracking |
| mariadb-galera | [![](https://img.shields.io/docker/v/instantlinux/mariadb-galera?sort=date)](https://microbadger.com/images/instantlinux/mariadb-galera "Version badge") | automatic cluster setup|
| nexus | ** | binary repo with docker registry |
| python-builder | [![](https://img.shields.io/docker/v/instantlinux/python-builder?sort=date)](https://microbadger.com/images/instantlinux/python-builder "Version badge") | CI testing for python|
| python-wsgi | [![](https://img.shields.io/docker/v/instantlinux/python-wsgi?sort=date)](https://microbadger.com/images/instantlinux/python-wsgi "Version badge") | WSGI runtime for python flask apps|
| wordpress | ** | |

**Networking and support**

| Service | Version | Notes |
| --- | --- | --- |
| authelia | ** | single-signon multi-factor auth |
| cloud | ** | nextcloud, private sync like Apple iCloud |
| docs | [![](https://img.shields.io/docker/v/instantlinux/open-xchange-appsuite?sort=date)](https://microbadger.com/images/instantlinux/open-xchange-appsuite "Version badge") | OX Appsuite, private cloud like Google Docs |
| data-sync | [![](https://img.shields.io/docker/v/instantlinux/data-sync?sort=date)](https://microbadger.com/images/instantlinux/data-sync "Version badge") | poor-man's SAN for persistent storage |
| duplicati | [![](https://img.shields.io/docker/v/instantlinux/duplicati?sort=date)](https://microbadger.com/images/instantlinux/duplicati "Version badge") | backups |
| ez-ipupdate | [![](https://img.shields.io/docker/v/instantlinux/ez-ipupdate?sort=date)](https://microbadger.com/images/instantlinux/ez-ipupdate "Version badge") | Dynamic DNS client |
| haproxy-keepalived | [![](https://img.shields.io/docker/v/instantlinux/haproxy-keepalived?sort=date)](https://microbadger.com/images/instantlinux/haproxy-keepalived "Version badge") | load balancer |
| guacamole | ** | authenticated remote-desktop server |
| logspout | ** | central logging for Docker |
| mysqldump | [![](https://img.shields.io/docker/v/instantlinux/mysqldump?sort=date)](https://microbadger.com/images/instantlinux/mysqldump "Version badge") | per-database alternative to xtrabackup |
| nagiosql | [![](https://img.shields.io/docker/v/instantlinux/nagiosql?sort=date)](https://microbadger.com/images/instantlinux/nagiosql "Version badge") | NagiosQL with Nagios Core v4 for monitoring |
| nut-upsd | [![](https://img.shields.io/docker/v/instantlinux/nut-upsd?sort=date)](https://microbadger.com/images/instantlinux/nut-upsd "Version badge") | Network UPS Tools |
| rsyslogd | [![](https://img.shields.io/docker/v/instantlinux/rsyslogd?sort=date)](https://microbadger.com/images/instantlinux/rsyslogd "Version badge") | logger in a 13MB image |
| samba | [![](https://img.shields.io/docker/v/instantlinux/samba?sort=date)](https://microbadger.com/images/instantlinux/samba "Version badge") | file server |
| samba-dc | [![](https://img.shields.io/docker/v/instantlinux/samba-dc?sort=date)](https://microbadger.com/images/instantlinux/samba-dc "Version badge") | Active-Directory compatible domain controller |
| [secondshot](https://github.com/instantlinux/secondshot) | [![](https://img.shields.io/docker/v/instantlinux/secondshot?sort=date)](https://microbadger.com/images/instantlinux/secondshot "Version badge") | rsnapshot-based backups |
| splunk | ** | the free version |

**Email**

| Service | Version | Notes |
| --- | --- | --- |
| blacklist | [![](https://img.shields.io/docker/v/instantlinux/blacklist?sort=date)](https://microbadger.com/images/instantlinux/blacklist "Version badge") | a local rbldnsd for spam control |
| dovecot | [![](https://img.shields.io/docker/v/instantlinux/dovecot?sort=date)](https://microbadger.com/images/instantlinux/dovecot "Version badge") | imapd server |
| postfix | [![](https://img.shields.io/docker/v/instantlinux/postfix?sort=date)](https://microbadger.com/images/instantlinux/postfix "Version badge") | compact general-purpose image in 11MB |
| postfix-python | [![](https://img.shields.io/docker/v/instantlinux/postfix-python?sort=date)](https://microbadger.com/images/instantlinux/postfix-python "Version badge") | postfix with spam-control scripts |
| rainloop | ** | webmail imapd-client server |
| spamassassin | [![](https://img.shields.io/docker/v/instantlinux/spamassassin?sort=date)](https://microbadger.com/images/instantlinux/spamassassin "Version badge") | spam control daemon |

**Entertainment**

| Service | Version | Notes |
| --- | --- | --- |
| davite | [![](https://img.shields.io/docker/v/instantlinux/davite?sort=date)](https://microbadger.com/images/instantlinux/davite "Version badge") | party-invites manager like eVite |
| mt-daapd | [![](https://img.shields.io/docker/v/instantlinux/mt-daapd?sort=date)](https://microbadger.com/images/instantlinux/mt-daapd "Version badge") | iTunes server |
| mythtv-backend | [![](https://img.shields.io/docker/v/instantlinux/mythtv-backend?sort=date)](https://microbadger.com/images/instantlinux/mythtv-backend "Version badge") | MythTV backend |
| weewx | [![](https://img.shields.io/docker/v/instantlinux/weewx?sort=date)](https://microbadger.com/images/instantlinux/weewx "Version badge") | Weather station software (Davis VantagePro2 etc.) |
| wxcam-upload | [![](https://img.shields.io/docker/v/instantlinux/wxcam-upload?sort=date)](https://microbadger.com/images/instantlinux/wxcam-upload "Version badge") | Upload webcam images to Weather Underground |

### Credits

Thank you to the following contributors!

* [Chad Hedstrom](https://github.com/Hadlock) - [personal site](http://nearlydeaf.com/)
* [Sean Mollet](https://github.com/SeanMollet)
* [Juan Manuel Carrillo Moreno](https://github.com/inetshell) - [personal site](https://wiki.inetshell.mx/)
* [nicxvan]( https://github.com/nicxvan)
* [Frank Riley](https://github.com/fhriley)
* [Devin Bayer](https://github.com/akvadrako)

Contents created 2017-20 under [Apache 2.0 License](https://www.apache.org/licenses/LICENSE-2.0) by Rich Braun.
