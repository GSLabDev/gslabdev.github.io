---
layout: post
title: "Open Source Contribution to Docker"
date: 2017-02-28 16:54:46
author: Milind Chawre
categories:
- blog
- Docker
- Development
img:
thumb: thumb02.jpg
---

<b>Docker</b> is an open platform for developing, shipping, and running applications. Docker enables you to separate your applications from your infrastructure so you can deliver software quickly. With Docker, you can manage your infrastructure in the same ways you manage your applications. In past, there were physical servers running application. Then virtualization changed this way of running application by having virtual servers running these applications. Now, Docker enables the creation of application containers that are much more efficient than running separate virtual machines.<!--more-->In a very short period of time, docker has witnessed large community support which includes active contribution from industry leaders like Google, RedHat, etc. There are around 1000 active community contributors to docker repository, 100000+ dockerized apps on docker hub, 50,000 third-party projects on GitHub using Docker. Many software giants are playing with docker eco-system to evaluate if they can containerize theirs applications. Cloud-vendors like Microsoft Azure, Amazon have enabled containerization support in their cloud platforms using docker. Docker is also natively supported by openstack. Google also built management suit called kubernetes, which supports docker. Almost all major players in industry are already involved or trying to be part of docker eco-system in one or other way. So it’s currently a trending technology which experts claim is here to stay.
</br>
To get acquainted with this trending technology, we proactively started exploring docker and playing around with its usecases. To further build the expertise, we started taking up some issues and try fixing them. Here is the glance at our contributions so far 

1. **Hostname resolution for local NFS volumes:** 
   Docker enables to mount NFS volumes inside containers. This functionality limits us to use only IP addresses to identify NFS volumes. In production, common practice is to address NFS volumes with hostname instead. Thus we added a feature in docker that would enable address resolution for NFS volumes from docker via all means host names, DNS names, IP addresses.
   </br>
   Issue : https://github.com/docker/docker/issues/26639
   PR : https://github.com/docker/docker/pull/27329

2. **Max restart time support for docker container:**
   Docker offers restart policy, which defines whether to restart the container after it crashes. As per the restart policy, the failed container will be restarted after a specified interval. If the restart fails, the time period of restart interval will be doubled. As there no upper bound to this time interval, the container may not be restarted for days or weeks if it is failing continuously. We solved this issue by keeping an upperbound to this restart interval to be a maximum of 1 minute.
   </br>
   Issue : https://github.com/docker/docker/issues/30503 
   PR : https://github.com/docker/docker/pull/30683

3. **Improved docker cli help:**
   Few of the docker cli commands were missing help for the allowed time units input. We added explicit help specifying all the valid time units. Default values for some docker cli input parameters were missing and were unknown to the user. So we identified default values for various parameters and their meanings. We updated docker cli help to reflect the same. 
   </br>
   Issue : https://github.com/docker/docker/issues/24083 
   PR : https://github.com/docker/docker/pull/27733 
   Issue : https://github.com/docker/docker/issues/27798 
   PR : https://github.com/docker/docker/pull/27947

4. **Remove obsolete docker documentation/code:** 
   In docker remote API, login token name registryToken was replaced by identityToken. But the documentation was still holding reference to older login token name to registryToken. We updated the documentation to make it consistent with the code. 
   </br>
   Issue : https://github.com/docker/docker/issues/27095 
   PR : https://github.com/docker/docker/pull/27341 
   
   Removed unused configurations for fluentd logging driver. 
   </br>
   Issue : https://github.com/docker/docker/issues/21803 
   PR : https://github.com/docker/docker/pull/27986 
   
   Removed bad references in docker volume documentation.
   </br>
   Issue : https://github.com/docker/docker/issues/26818
   PR : https://github.com/docker/docker.github.io/pull/232

5. **Clarifying docker behaviour in documentation:**
   Docker allows to attach a network to created/stopped container. But when we inspect the container, network information is missing. This is because network is attached to the container only when its run. This information was missing from docker documentation, which we added. 
   </br>
   Issue : https://github.com/docker/docker/issues/28600 
   PR : https://github.com/docker/docker/pull/28602 
   
   Docker added new feature called live-restore, this functionality is supported for linux containers only. The functionality is not implemented for windows containers. We added this note in live-restore features documentation. 
   </br>
   Issue : https://github.com/docker/docker/issues/28295 
   PRs : https://github.com/docker/docker/pull/28384 
   https://github.com/docker/docker.github.io/pull/564
   
   There are two conflicting options in dockerd -- ip-masq and -- iptables. -- ip-masq which automatically adds iptables rules to enable external connectivity and -- iptables to enable or disable dockerd from automatically updating iptables rules. If iptables is set to false and ip masq to true, iptables option takes precedence and dockerd does not automatically update the iptables rules. We documented this behaviour in dockerd help and documentation.
   </br>
   Issue : https://github.com/docker/docker/issues/28133
   PR : https://github.com/docker/docker/pull/28607

**References:**
</br>
https://docs.docker.com/opensource/code/
https://dockercommunity.slack.com/

