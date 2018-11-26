# CON301-R - Mastering Kubernetes on AWS
## Yaniv Donenfeld - Sr. Business Development Manager
## Karl D'Adamo - Senior Director of Engineering, Snapchat
### November 26, 2018

51% of kubernetes clusters are run on aws

NodePort allocate a specific port for a service, and it will allow you to define a port and all nodes for that service will receive traffic on that port, and use it for the configured servicel. Nodes can forward to other nodes that actually contain pods with that service associated with the port

Another option is an ingress object using an ingress object controller. This avoids the overhead associated with node port navigating through the node ip, then to the pod

See iam access info in picture.

Logging: workers

look into using fluentd couldwatch plugin. see info in picture
https://eksworkshop.com/logging

CON361  - Deep Dive on Amazon EKS

---
Snapchat info for use of EKS:
How to manage the scaling of the engineering organizations
This guy manages teams that build internal apps for the Snapchat engineering teams

Choose a vendor over roll your own (vanilla kubernetes vs EKS). Choose a vendor if the cost delta is small, and the vendor is providing a service above the vanilla install

~1600 APIs in snap
plan is to have 200-400 services, running on kubernetes / EKS
7500 cores, 250k transactions / sec

consider redundancy and failover / backup strategy based on services that can handle bulk loading (lower pri)

optimizing the instance types and counts (fewer, larger instances saved them $)

reducing the amount of overprovisioning that is going on.

---
# NET-312 - A day in the life of a cloud network eng at netlix
### November 26, 2018



