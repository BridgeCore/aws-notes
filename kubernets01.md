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

---
# DEV-316 - advanced devops
review slides, really good slides.
Source

use code pipeline to manage the process (states, with tasks)
DEV309 has details

deploy to prod w/ code deploy

code pipeline sounds like a competitor to jenkins

1. look up
2. look up
3. Rollback when deployment fails

---
# ENT-311 Enterprise devops

1. enablement and repeatability
2. speed - guardrails required
3. inclusiveness
4. focus on differentiating factors
5. Built-in as opposed to bolt on
  * visibility
  * compliance
  * ...
---
# secure your aws resources like  pro
too basic overview of iam and policies

---
# serverless arch patterns
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




