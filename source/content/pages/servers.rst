Servers
=======

:category: page
:slug: servers
:sort-order: 02

There are four options for setting up infrastructure to serve a
web application:

1. "Bare metal" servers

2. Virtualized servers

3. Infrastructure-as-a-service

4. Platform-as-a-service

Bare metal
----------
The term *bare metal* refers to purchasing the actual hardware and hooking 
it up to the Internet either through a business-class internet service 
provider (ISP) or 
`co-locating the server <http://webdesign.about.com/od/colocation/a/what_colocation.htm>`_ with other servers. A "business-class" ISP is necessary because
most residential Internet service agreements prohibt and will eventually
block traffic to web servers. You may be able to get away with low traffic
volume but if your site serves a lot of traffic it will catch an ISPs
filters.

The bare metal option offers the most control over the server configuration,
usually has the highest performance for the price, but also is the most 
expensive upfront option and the highest ongoing maintenance. With bare
metal servers the ongoing operating cost is the electricity the server(s) 
use as well as handling repairs when server components malfunction. You're
taking on manual labor working with hardware as well as the rest of the
software stack.

Buy actual hardware from a vendor either pre-built or as a collection of 
components that you assemble yourself. Here is an 
`example of a server buildout <http://duartes.org/gustavo/blog/post/building-a-quad-core-server>`_. The post is a couple of years old but those are the
rough components you need to put together your own server. You can also buy 
pre-configured servers from Dell or HP. Those servers tend to be in
smaller case form factors (called "blades") but are correspondingly more 
expensive than putting off-the-shelf components together yourself.


Virtualized servers
-------------------
Virtual private servers (VPSs) are slices of hardware on top of a larger
bare metal server. Virtualization software such as 
`Xen <http://www.xen.org/>`_ and
`VMWare <http://www.vmware.com/virtualization/what-is-virtualization.html>`_
allow providers such as `Linode <http://www.linode.com/>`_ and
`prgmr <http://prgmr.com/xen/>`_ (as well as a many others) to provide
fractions of a full server that appear as their own instances. For example,
a server with an 8-core Xeon processor and 16 gigabytes of memory can be
sliced into 8 pieces with the equivalent of 1-core and 2 gigabytes of
memory.

The primary disadvantage of virtualized servers is that there is resource
overhead in the virtualization process. In addition, physical constraints
such as heavy I/O operations by a single virtualized instance on persistent 
storage can cause performance bottlenecks for other virtualized instances on
the shared server. Choosing virtualized server hosting should be based on
your needs for urgency of service ticket requests and the frequency you
require for ongoing maintenance such as persistent storage backups.


Infrastructure-as-a-service
---------------------------
Infrastructure-as-a-service (IaaS) overlaps with virtualized servers 
because the resources are often presented in the same way. The 
difference between virtualized servers and IaaS is the granularity of the
billing cycle. IaaS generally encourages a finer granularity based on minutes
or hours of server usage instead of on monthly billing cycles.

IaaS can be used in combination with virtualized servers to provide 
dynamic upscaling for heavy traffic. When traffic is low then virtualized
servers can solely be used. This combination of resources reduces cost at
the expense of greater complexity in the dynamically scaled infrastructure. 

The most common IaaS platforms are 
`Amazon Web Services <http://aws.amazon.com/>`_ and 
`Rackspace Cloud <http://www.rackspace.com/cloud/>`_.

The disadvantage to IaaS platforms is the lock-in if you have to write
custom code to deploy, dynamically scale, and generally understand your
infrastructure. Every platform has its quirks. For example, 
Amazon's standard `Elastic Block Store <http://aws.amazon.com/ebs/>`_ storage
infrastructure has at least an order of magnitude worse I/O throughput 
than working with your local disk. Your application's database queries may 
work great locally but then when you deploy the performance is inadequate.
Amazon has `higher throughput EBS instances <http://aws.amazon.com/about-aws/whats-new/2012/07/31/announcing-provisioned-iops-for-amazon-ebs/>`_ 
but you will pay correspondingly more for them. EBS throughput is just 
one of many quirks you need to understand before committing to an 
IaaS platform.


Platform-as-a-service
---------------------
A platform-as-a-service (PaaS) provides infrastructure and a software layer
on which a web application is deployed. The PaaS layer defines how the 
application accesses resources such as computing time, files, and 
external services. The PaaS provides a higher-level abstraction for working
with computing resources than deploying an application to a server or IaaS.

A PaaS makes deployment and operations easier because it forces the developer
to conform applications to the PaaS architecture.

`Heroku <http://www.heroku.com/>`_, 
`Google App Engine <https://developers.google.com/appengine/>`_,
`Gondor <https://gondor.io/>`_, and
`OpenShift <https://openshift.redhat.com/community/get-started/python>`_ are
platform-as-services that support Python web applications. Each one requires
varying tradeoffs to deploy to their respective platforms.

If you go the PaaS route, you can skip over the operating system and web
server sections because they are baked into PaaS offerings. PaaS offerings
generally start at the WSGI server layer.


Server Monitoring
-----------------
Server uptime, that the server is powered and reachable over the network,
must be monitored on this level. That means an outside host must perform
the monitoring to ensure availablity. Other attributes of the server such
as CPU and memory utilization are grouped under the "Operating System"
section.


Server Resources
----------------
`How to set up a safe and secure Web server <http://arstechnica.com/gadgets/2012/11/how-to-set-up-a-safe-and-secure-web-server/>`_ (Ars Technica)

`Staging Servers, Source Control & Deploy Workflows, And Other Stuff Nobody Teaches You <http://www.kalzumeus.com/2010/12/12/staging-servers-source-control-deploy-workflows-and-other-stuff-nobody-teaches-you/>`_ (Patrick McKenzie)

`Choosing Heroku <http://rdegges.com/devops-django-part-4-choosing-heroku>`_
(Randall Degges)

`Choosing a low cost VPS <http://blog.redfern.me/choosing-a-low-cost-vps/>`_ 

`boto <https://github.com/boto/boto>`_ is an amazing Python library for
working with Amazon Web Services
