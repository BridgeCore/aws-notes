# CON301-R - Mastering Kubernetes on AWS
**Yaniv Donenfeld** - Sr. Business Development Manager
**Karl D'Adamo** - Senior Director of Engineering, Snapchat
*November 26, 2018*

51% of kubernetes clusters are run on aws

NodePort allocate a specific port for a service, and it will allow you to define a port and all nodes for that service will receive traffic on that port, and use it for the configured servicel. Nodes can forward to other nodes that actually contain pods with that service associated with the port

Another option is an ingress object using an ingress object controller. This avoids the overhead associated with node port navigating through the node ip, then to the pod

See iam access info in picture.

Logging: workers

look into using fluentd couldwatch plugin. see info in picture
https://eksworkshop.com/logging

another good session to review is: 
CON361  - Deep Dive on Amazon EKS

### Snapchat info for use of EKS:
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

Awesome presentation. Good examples of how to overcome huge scale tech problems.

---
# DEV-317 - Advanced Continuous Delivery Best Practices
review slides, really good slides.

use code pipeline to manage the process (states, with tasks)
review session DEV309 for additional details

deploy to prod w/ code deploy

code pipeline sounds like a competitor to jenkins

1. look up
2. look up
3. Rollback when deployment fails

---
# ENT-311 Enterprise devops patterns

1. enablement and repeatability
2. speed - guardrails required
3. inclusiveness
4. focus on differentiating factors
5. Built-in as opposed to bolt on
  * visibility
  * compliance
  * ...
---
# SEC203 - A Practitioners guide to securing your cloud like an expert
too basic overview of iam and policies

---
# ARC305 - Serverless arch patterns and best practices
### November 26, 2018

see slides:
github.com/alexcasalboni/

## best practices
* put dependencies in a separate /lib directory
* dependency injection is bad for quick starts (use dagger2 over sprint boot)
* use jackson-jr for data binding (java)
* use env vars to modify operational behaviour (for fastest secrets mgmt)
* minimize package size

SAM for local cli testing of lambda functions
AWS Cloud9 (cloud based IDE)
AWS CodeStar will create environment, ide/code build/code deploy/etc

1. Web Application Pattern
cloudfront and s3 for static
api gateway to lambda to dynamodb
cognito for user mgmt
edge optimized (cloudfront distribution)
check lambda@edge use cases and blueprints (search for cloudfront)
private API (can be used through direct connect

GraphQL is implemented in AWS AppSync

2. Stream Processing Patterns
Kineses
  * video streams
  * data streams
  * data firehose
  * dta analytics

3. Data lakes
ingest into S3 from Kinesis or IoT or Direct connect (or sftp)
catalog and search data using dynamodb, glue, ES
analytics and processing (lambda, etc., s3 select, quicksight, athena, lambda, sagemaker, EMR, Glue [ETL])
https://aws.amazon.com/answers/big-dta/data-lake-solution/
athena:
SELECT gram, year, sum(count) FROM ngram WHERE gram = 'just say no' GROPU BY gram, year ORDER BY year ASC;
reduce cost for athena queries by reducing files scanned:
s3://bucket/flight/parquet/year=2018/month=11/day=25

4. Machine Learning
frameworks (i.e. caffe or tensorflow)
Platforms (sagemaker, Mechanical Turk)
API driven services:
- vision (amazon rekognition)
- language (polly, transcrie, translate, comprehend)
- chatbots, Amazon Lex
---
# CON307-S - Production-Ready Environments for Kubernetes
just a big sales pitch for cisco

---
# CMP 310-S Application Portability with Kubernetes
VMWare sales pitch. Good functionality for managing the number of nodes deployed in a kubernetes cluster. Similar functionality to openshift

---
# CON305 - Get SaaSy with RH Openshift on AWS

bad link --> http://bit.ly/wI18UMw

install to dev environment:
https://github.com/fusor/catasb

https://aws.amazon.com/quickstart/architecture/openshift

openshift service catalog allows you bind aws services to openshift applications
demo w/ s3, ml

Openshift 3.11 info:
* multiple consoles
  * service catalog
  * application console
  * cluster console
* visibility into nodes
  * resource utilization for nodes
* rbac users and sercie accounts with a specific role
  * visually audit a role's verbs and objects
    *  cluster event stream
* operator sdk
* jenkins plugins
* AWS atoscale groups
* router improvements
    * http/2
    * reload config changes
    * ssl/tls cert validation
    * EFK logging of router
* security
  * define rules to enforce compliance
* prometheus monitoring is built in and GA
* logging
  * ES 5 and Kibana 5

quickstart
https://aws.amazon.com/quickstart/architecture/openshift

---
# CON205-R1 - Getting started with Kubernetes on AWS
Workshop
other 
CON 323
CON 411
---
# DEV306 
workshop on monitoring