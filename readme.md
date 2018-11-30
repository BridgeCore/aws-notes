# CON301-R - Mastering Kubernetes on AWS
**Yaniv Donenfeld** - Sr. Business Development Manager
**Karl D'Adamo** - Senior Director of Engineering, Snapchat
*November 26, 2018*
https://www.youtube.com/watch?v=8OPkt93WyPA


51% of kubernetes clusters are run on aws

NodePort allocate a specific port for a service, and it will allow you to define a port and all nodes for that service will receive traffic on that port, and use it for the configured servicel. Nodes can forward to other nodes that actually contain pods with that service associated with the port

Another option is an ingress object using an ingress object controller. This avoids the overhead associated with node port navigating through the node ip, then to the pod

See iam access info in picture.

Logging: workers

look into using fluentd couldwatch plugin. see info in picture
https://eksworkshop.com/logging

another good session to review is: 
CON361  - Deep Dive on Amazon EKS

**Snapchat info for use of EKS:**
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
https://www.youtube.com/watch?v=95nfMj4PVDA

Awesome presentation. Good examples of how to overcome huge scale tech problems.

---
# DEV-317 - Advanced Continuous Delivery Best Practices
https://www.youtube.com/watch?v=Jnl29J3RJQ4

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
https://www.youtube.com/watch?v=bjOEDItOdjI

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
https://www.youtube.com/watch?v=5UDSxV9pbnU

too basic overview of iam and policies

---
# ARC305 - Serverless arch patterns and best practices
*November 26, 2018*
https://www.youtube.com/watch?v=08AjVGGQaKQ

see slides:
github.com/alexcasalboni/

**best practices**
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
https://www.youtube.com/watch?v=AU7EBRViwhE

VMWare sales pitch. Good functionality for managing the number of nodes deployed in a kubernetes cluster. Similar functionality to openshift

---
# CON305 - Get SaaSy with RH Openshift on AWS
https://www.youtube.com/watch?v=w7zeXk6Kggk

http://bit.ly/2I18UMw

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
# keynote

---
# CON205-R1 - Getting started with Kubernetes on AWS
Workshop - no video
other 
CON 323
CON 411

---
# DEV306
workshop - no video

lab: https://s3-us-west-2.amazonaws.com/aws-well-architected-labs/Operations/DEV306CloudWatch.html

Will be posted to github aws well architected framework

**Design Principles**
* perform operations as code
* annotated documentation
* make frequent, small, reversible changes
* refine ops procedures frequently
* antisipate failure (have a pre-mortem to determine risk, and drive out the risk)
* learn from all operational failures

**reasons to change**
1. something you want
2. something to fix
3. to satisfy requirements (regulatory)
Otherwise you shouldn't be making the change (example, daily patching will break things w/ no value if your compliance requirement is to patch monthly)

---
# NET303 Advanced VPC Design and New Capabilities

updates on new VPC capabilities
VPC sharing allows multiple accounts to share a VPC. There is one account that is the owner, and that defines the CIDR block. The owner defines route tables. But the participants own the resources. The owner cannot delete participant's resources.
Must be in the same AWS organization
no VPC peering required
No AZ cost for data transfer

VPC Sharing
https://amzn.to/2Aovw2Z

https://amzn.to/2FI3y90

Hybrid Clouds (using R53 over hybrid)
https://amzn.to/2ByEw7s

Client VPN
allows (laptop to VPN into a VPC)

Client VPN session: NET304

VPC to VPC connections using VPC Peering can be complex with lots of VPCs
for full Mesh VPC peering, n(n-1)/2 VPC Peering COnnections
i.e. 10 VPCs, fully meshed is 45 VPC Peering connections
VPC route limits constrain the amount of VPC peering connections
using aws Transit Gateway (TGW)
VPCs (or direct connect) are attached to a TGW. 
Transit Gateways allow for a lot more flexibility of VPC connections (and on prem connection options)

---
# STG403 - Advanced Storage w/ s3 and glacier
https://stg403.s3.amazonaws.com/guide.html

putting in glacier
1. use lifecycle rule
2. s3 put opbject to glacier
3. s3 put copy to glacier
4. Cross Region Replication w/ destination bucket lifecycle rule to add to glacier

* s3 now provides restore notifications (SNS, SQS, Lambda)

**two modes for s3 object locks**
1. **Governance mode** (specific IAM permisssions to remove WORM protections)
2. **Compliance Mode** (no API/user to remove WORM protection)

---
# keynote 2
lots of feature announcements

---

#DEV305 - AWS DevOps Essensitals and intro workshop on CI/CD
workshop, no video
https://github.com/awslabs/aws-devops-essential

https://bit.ly/2rMcMXF

my run notes:
user: devops
https://git-codecommit.us-east-1.amazonaws.com/v1/repos/WebAppRepo

devops-at-993037553293
gn+j7HkU0+yxbgVoaJjyjFwEBDxBk33icDAo8c4lKPg=

bucket: cicd-workshop-us-east-1-993037553293

BuildRole arn:
arn:aws:iam::993037553293:role/DevopsWorkshop-roles-BuildTrustRole-G2Z50PP9UST1

first build id:
"id": "devops-webapp-project:862b2a41-9892-4b28-b025-5da91d55554c", 


codedeploy arn:
arn:aws:iam::993037553293:role/DevopsWorkshop-roles-DeployTrustRole-TVRSNZCD49GD

2nd deploy's etag:
bf67a844a5f08ce1b62ffb5adb338530-3

code deploy arn:
arn:aws:iam::993037553293:role/DevopsWorkshop-roles-DeployTrustRole-TVRSNZCD49GD


---

# SRV 314 - Wecuring Serverless Applications and AWS Lambda

https://amzn.to/serverless-security

my items
AuroraEndpoint:
secure-serverless-auroradbcluster-1wuw7v16oragd.cluster-czwk5zhxulgp.us-east-1.rds.amazonaws.com

s3 bucket:
secure-serverless-deploymentss3bucket-rri7m5jo1u7m

stack endpoint:
https://a0c9yrznk6.execute-api.us-east-1.amazonaws.com/dev/

domain-name:
https://custom-unicorn-jake.auth.us-east-1.amazoncognito.com

App client id:
26ilrkqhpeaju6gdvvlqi6j7j

App client secret:
11erele327r9ca6pchalav6q5qhnsoam2mv7rpq23d53is9iqpoc

Jake is Good Company:
{
    "ClientID": "3kf3pm9s1dv57uiua1h3lvpmuk",
    "ClientSecret": "keqnjb2mj1g2sgop23505103l5ulp89tnije6okdfc9fk2pkukq"
}

current risk priority:
owasp.org

scenario:
wildrydes.com expansion for customization

SkyMiles®#9182501511 >