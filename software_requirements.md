# Software requirements

Last Updated: 2024-06-

Before you install IBM Cloud Pak for Data, review the software requirements for the control plane, the shared cluster
components, and the services that you plan to install, and review the supported web browsers.

## Cloud Pak for Data platform software requirements

You must have the following software to install Cloud Pak for Data:

**Red Hat® OpenShift® Container Platform**

```
For entitlement information see Licenses and entitlements.
```
```
Cloud Pak for Data supports the following versions of Red Hat OpenShift Container Platform. (Cloud Pak for Data
supports the same operating system requirements as Red Hat OpenShift Container Platform.)
```
- Cloud Pak for Data platform software requirements
- Supported networking protocols
- Shared cluster component software requirements
- Service software requirements
- Supported web browsers

```
Important: Cloud Pak for Data supports only the specified releases of Red Hat OpenShift Container
Platform.
Different versions of Cloud Pak for Data support different versions of Red Hat OpenShift Container Platform.
```
```
Version Learn more Cluster sizing guidance
Version
4.12.
or later
fixes
```
```
For details, see the Red Hat OpenShift Container
Platform documentation :
```
```
Refer to the Cloud Pak for Data platform
hardware requirements as you configure your
```
- Installation overview cluster.
    Selecting a cluster installation method and
    preparing it for users

### –

- Control plane node sizing

```
Restriction: Data Virtualization and
Db2 Big SQL are not supported on Red
Hat OpenShift Container Platform
Version 4.12. If you plan to install
either of these services, you must
install Red Hat OpenShift Container
Platform Version 4.14 or later.
```

**Kubernetes Metrics Server**

```
If you do not enable the default monitoring stack on your Red Hat OpenShift Container Platform cluster and you want
to gather use metrics for your pods and nodes, install Kubernetes Metrics Server.
```
## Supported networking protocols

IBM Cloud Pak for Data can run on the following networking protocols:

For more information, see _Converting to IPv4/IPv6 dual-stack networking_ in the Red Hat OpenShift Container Platform
documentation:

## Shared cluster component software requirements

There are no additional software requirements for:

## Service software requirements

```
Version Learn more Cluster sizing guidance
Version
4.14.
or later
fixes
```
```
For details, see the Red Hat OpenShift Container
Platform documentation :
```
```
Refer to the Cloud Pak for Data platform
hardware requirements as you configure your
cluster.
```
```
Version
4.15.
or later
fixes
```
```
For details, see the Red Hat OpenShift Container
Platform documentation :
```
```
Refer to the Cloud Pak for Data platform
hardware requirements as you configure your
cluster.
```
- Installation overview
    Selecting a cluster installation method and
    preparing it for users

### –

- Control plane node sizing
- Installation overview
    Selecting a cluster installation method and
    preparing it for users

### –

- Control plane node sizing

```
Important: If you do not enable the default monitoring stack or install Kubernetes Metrics Server, the
platform monitoring features in Cloud Pak for Data will not work.
```
- IPv4 single-stack network
- IPv4/IPv6 dual-stack network
- Version 4.
- Version 4.
- Version 4.
- Scheduling service
- Common core services


Use this table to determine whether the service that you want to install depends on other software being available:

- Some services require other software to be installed outside of Cloud Pak for Data (marked as external dependencies)
    Some services require other Cloud Pak for Data services to be installed as prerequisites or to support specific
    functionality (marked as service dependencies)

### –

```
Some services require other underlying components, which the service installs if needed (marked as component
dependencies)
```
### –

```
Service
```
```
External
dependencies Service dependencies Component dependencies
AI Factsheets None The service does not
have any service
dependencies.
To implement a
complete AI
governance solution,
you must install the
following services:
```
```
If you install AI
Factsheets with only
Watson Studio, you can
create AI use cases in
only one catalog.
```
```
The service automatically installs the
following dependencies if they are
not already installed:
```
```
Anaconda
Repository for IBM
Cloud Pak for Data
```
```
For details, see the
Anaconda
installation
requirements.
```
```
None None
```
```
Analytics Engine
powered by Apache
Spark
```
```
None None None
```
```
Cognos Analytics To use Cognos
Analytics, you must
have:
```
```
None The service automatically installs the
following dependencies if they are
not already installed:
```
- OpenPages
    IBM Knowledge
    Catalog

### –

- Watson OpenScale
    Watson Machine
    Learning

### –

- Watson Studio
    - Common core services (ccs)
       OpenSearch
       (opencontent_elasticsearch)

### –

```
A content store for
configuration data,
global settings,
data server
connections, and
product-specific
content. The
```
- –Common core services (ccs)
    OpenSearch
    (opencontent_elasticsearch)

### –


**Service**

```
External
dependencies Service dependencies Component dependencies
```
Cognos Dashboards None None The service automatically installs the
following dependencies if they are
not already installed:

Data Gate To use this service,
you must have:

```
To use this service, you
must have at least one
instance of a
supported, integrated
database:
```
```
None
```
```
content store can
be an integrated
Db2 database or
an external
relational
database. For
details, see
Configuring the
content store for
Cognos Analytics.
A database for
audit records. You
can optionally
store the audit
records in the
content store. For
details, see
Provisioning the
Cognos Analytics
instance.
```
### –

```
An SMTP server, if
you want to use
the email
notification
feature. For
details, see
Provisioning the
Cognos Analytics
instance.
```
### –

- Common core services (ccs)
    OpenSearch
    (opencontent_elasticsearch)

### –

- Redis (ibm_redis_cp)

```
IBM® z/OS V2.
(5650-ZOS) or
later.
```
### –

```
Db2 for z/OS,
either:
```
### –

### ▪ V12 (5650-DB

- Db
- Db2 Warehouse


**Service**

```
External
dependencies Service dependencies Component dependencies
The following services
are not required but
provide additional
functionality:
```
Data Privacy None To install this service,
you must have the
following services
already installed:

```
None
```
```
or 5770-AF3)
with APAR fixes
installed and
running at
Function Level
505 or higher.
You find the list
of required
APAR fixes
here: Software
dependencies.
V13 (5698-DB
or 5698-DBV)
```
### ▪

```
Distributed data
facility (DDF) with
a secure port,
configured for
network
encryption through
AT-TLS. For details,
see Configuring
network access
between Data Gate
and IBM Z.
```
### –

```
IBM Knowledge
Catalog enables you
to automatically
publish metadata
about Data Gate
tables to catalogs.
```
### –

```
Analytics Engine
powered by Apache
Spark
```
### –

```
IBM Knowledge
Catalog or IBM
Knowledge Catalog
Premium
```
### –


**Service**

**External
dependencies Service dependencies Component dependencies**
Data Product Hub None The service
automatically installs
the following services if
they are not already
installed:

```
The service automatically installs the
following dependencies if they are
not already installed:
```
Data Refinery None None None

Data Replication None None The service automatically installs the
following dependencies if they are
not already installed:

DataStage None The following services
are not required but
provide additional
functionality:

```
The service automatically installs the
following dependencies if they are
not already installed:
```
Data Virtualization None The service
automatically installs
the following services if
they are not already
installed:

```
The service automatically installs the
following dependencies if they are
not already installed:
```
Db2 None The following services
are not required but
provide additional
functionality:

```
This service automatically installs
the following dependencies if they
are not already installed:
```
```
Analytics Engine
powered by Apache
Spark
```
### –

- Data Refinery
    - Common core services (ccs)
    - Db2 as a service (db2aaservice)
    - Db2U (db2u)
       OpenSearch
       (opencontent_elasticsearch)

### –

- Common core services (ccs)
    OpenSearch
    (opencontent_elasticsearch)

### –

```
Orchestration
Pipelines enables you
to convert DataStage
sequence jobs to
pipelines.
```
### –

- Common core services (ccs)
    OpenSearch
    (opencontent_elasticsearch)

### –

```
Db2 Data
Management Console
```
### –

- Common core services (ccs)
- Db2U (db2u)
    OpenSearch
    (opencontent_elasticsearch)

### –

- Redis (ibm_redis_cp)

```
Db2 Data
Management Console
provides:
```
### –

```
▪ A graphical user
```
- Db2U (db2u)


**Service**

```
External
dependencies Service dependencies Component dependencies
```
Db2 Big SQL To use Db2 Big SQL,
you must have
remote data storage,
such as:

```
The following services
are not required but
provide additional
functionality:
```
```
This service automatically installs
the following dependencies if they
are not already installed:
```
Db2 Data
Management
Console

```
None None This service automatically installs
the following dependencies if they
are not already installed:
```
Db2 Warehouse None The following services
are not required but
provide additional
functionality:

```
This service automatically installs
the following dependencies if they
are not already installed:
```
```
interface for SQL
execution
A runtime
monitoring
interface
```
### ▪

```
A Hadoop cluster
on Cloudera Data
Platform Version
7.1.
```
### –

```
Object storage
Db2 Big SQL
supports:
```
### –

```
IBM Cloud
Object Storage
```
### ▪

```
Amazon Web
Services object
storage
```
### ▪

```
IBM Storage
Scale object
storage
```
### ▪

```
Red Hat
OpenShift Data
Foundation
```
### ▪

```
Db2 Data
Management Console
provides:
```
### –

```
A graphical user
interface for SQL
execution
```
### ▪

```
A runtime
monitoring
interface
```
### ▪

- Db2U (db2u)
- Redis (ibm_redis_cp)

```
Db2 Data
Management Console
provides:
```
### –

```
A graphical user
interface for SQL
execution
```
### ▪

```
A runtime
monitoring
```
### ▪

- Db2U (db2u)


**Service**

```
External
dependencies Service dependencies Component dependencies
```
Decision
Optimization

```
None To install this service,
you must have the
following services
already installed:
```
```
None
```
EDB Postgres None None This service automatically installs
the following dependencies if they
are not already installed:

Execution Engine for
Apache Hadoop

```
To use this service,
you must have an
Execution Engine for
Apache Hadoop RPM
installation on a
Hadoop cluster.
```
```
To install this service,
you must have the
following services
already installed:
```
```
None
```
IBM Knowledge
Catalog

```
None The service
automatically installs
the following services if
they are not already
installed:
```
```
If you choose to install
the data quality feature,
the service
automatically installs
the following services if
they are not already
installed:
```
```
The following services
are not required but
provide additional
functionality:
```
```
The service automatically installs the
following dependencies if they are
not already installed:
```
```
If you choose to install the semantic
search and data lineage feature, the
service automatically installs the
following dependencies if they are
not already installed:
```
```
interface
```
- Watson Studio
    Watson Machine
    Learning

### –

```
Cloud Native PostgreSQL
(postgresql)
```
### –

- Watson Studio

```
Analytics Engine
powered by Apache
Spark
```
### –

- Data Refinery
- DataStage Enterprise
- Data Privacy
    - Common core services
    - Db2 as a service (db2aaservice)
    - Db2U (db2u)

```
FoundationDB
(opencontent_fdb)
```
### –


**Service**

```
External
dependencies Service dependencies Component dependencies
```
IBM Knowledge
Catalog Premium

```
To install this service,
you must install the
following operators:
```
```
For more information
on installing these
operators, see
Installing operators
for services that
require GPUs.
```
```
The service
automatically installs
the following services if
they are not already
installed:
```
```
If you choose to install
the data quality feature,
the service
automatically installs
the following services if
they are not already
installed:
```
```
The following services
are not required but
provide additional
functionality:
```
```
The service automatically installs the
following dependencies if they are
not already installed:
```
```
If you choose to install the semantic
search and data lineage feature, the
service automatically installs the
following dependencies if they are
not already installed:
```
```
MANTA Automated
Data Lineage
```
### –

```
Node Feature
Discovery
Operator
Install the stable
version of the
operator.
```
### –

### NVIDIA GPU

```
Operator
The version that
you install
depends on the
version of Red Hat
OpenShift
Container Platform
that you are
running:
```
### –

```
On OpenShift
4.12, use
v23.9.x or
v24.3.x
```
### ▪

```
On OpenShift
4.14, use
v23.9.x or
v24.3.x
```
### ▪

```
On OpenShift
4.15, use
v24.3.x
```
### ▪

```
Red Hat OpenShift
AI Operator
Version 2.8.
```
### –

```
Analytics Engine
powered by Apache
Spark
```
### –

- Data Refinery
- DataStage Enterprise
- Data Privacy
    MANTA Automated
    Data Lineage

### –

- Common core services
- Db2 as a service (db2aaservice)
- Db2U (db2u)
    Inference foundation models
    (watsonx_ai_ifm)

### –

```
OpenSearch
(opencontent_elasticsearch)
```
### –

```
FoundationDB (fdb_k8s and
opencontent_fdb)
```
### –


**Service**

**External
dependencies Service dependencies Component dependencies**
IBM Knowledge
Catalog Standard

```
To install this service,
you must install the
following operators:
```
```
For more information
on installing these
operators, see
Installing operators
for services that
require GPUs.
```
```
The service
automatically installs
the following services if
they are not already
installed:
```
```
The following services
are not required but
provide additional
functionality:
```
```
This service automatically installs
the following dependencies if they
are not already installed:
```
IBM Match 360 with
Watson

```
None The following service is
not required but
provides additional
functionality:
```
```
This service automatically installs
the following dependencies if they
are not already installed:
```
```
Node Feature
Discovery
Operator
Install the stable
version of the
operator.
```
### –

### NVIDIA GPU

```
Operator
The version that
you install
depends on the
version of Red Hat
OpenShift
Container Platform
that you are
running:
```
### –

```
On OpenShift
4.12, use
v23.9.x or
v24.3.x
```
### ▪

```
On OpenShift
4.14, use
v23.9.x or
v24.3.x
```
### ▪

```
On OpenShift
4.15, use
v24.3.x
```
### ▪

```
Red Hat OpenShift
AI Operator
Version 2.8.
```
### –

```
Analytics Engine
powered by Apache
Spark
```
### –

```
MANTA Automated
Data Lineage
```
### –

- Common core services (ccs)
- Db2 as a service (db2aaservice)
- Db2U (db2u)
    Inference foundation models
    (watsonx_ai_ifm)

### –

```
OpenSearch
(opencontent_elasticsearch)
```
### –

- Common core services (ccs)


**Service**

```
External
dependencies Service dependencies Component dependencies
```
Informix None None This service automatically installs
the following dependencies if they
are not already installed:

MANTA Automated
Data Lineage

```
None To install this service,
you must have one of
the following services
already installed:
```
```
None
```
MongoDB None None You must install the following
dependencies when you install the
service:

OpenPages If you prefer to
connect to an
external database
rather than having
OpenPages
automatically
provision a Db
database for you,
you must have one of
the following
databases:

```
The following services
are not required but
provide additional
functionality:
```
```
This service automatically installs
the following dependencies if they
are not already installed:
```
```
IBM Knowledge
Catalog enables key
IBM Match 360
capabilities such as
profiling,
automapping, data
quality workflows,
and data governance.
```
- FoundationDB (fdb_k8s and
    opencontent_fdb)

### –

```
OpenSearch
(opencontent_elasticsearch)
```
### –

```
RabbitMQ
(opencontent_rabbitmq)
```
### –

- Redis (opencontent_redis)
- informix

```
IBM Knowledge
Catalog
```
### –

```
IBM Knowledge
Catalog Premium
```
### –

```
IBM Knowledge
Catalog Standard
```
### –

- mongodb
- IBM Db2 on Linux
- Oracle

```
AI Factsheets
enables you to review
machine learning
models and related
activities as part of
enterprise risk and
compliance
monitoring.
```
### –

- Cognos Analytics
- watsonx Assistant
- Watson Discovery
- IBM Knowledge
    - Db2 as a service (db2aaservice)
    - Db2U (db2u)
       RabbitMQ
       (opencontent_rabbitmq)

### –


**Service**

```
External
dependencies Service dependencies Component dependencies
```
Orchestration
Pipelines

```
None The following services
are not required but
provide additional
nodes when they are
installed:
```
```
The service automatically installs the
following dependencies if they are
not already installed:
```
Planning Analytics If you want to use
Microsoft Excel, you
must have the
Planning Analytics
for Microsoft Excel
plug-in.

```
None None
```
Product Master If you want to
connect to a
database outside of
Cloud Pak for Data, it
must be an IBM Db
or Oracle database.

```
If you want to connect
to an integrated
database, you must
have the following
service already
installed:
```
```
None
```
RStudio® Server
Runtimes

```
None To install this service,
you must have the
following service
already installed:
```
```
None
```
SPSS Modeler None To install this service,
you must have the
following services
already installed:

```
This service automatically installs
the following dependencies if they
are not already installed:
```
Synthetic Data
Generator

```
None None This service automatically installs
the following dependencies if they
are not already installed:
```
```
Catalog
```
- Watson OpenScale
- DataStage
    Watson Machine
    Learning

### –

- Common core services (ccs)
    OpenSearch
    (opencontent_elasticsearch)

### –

- Db
- Watson Studio
- Watson Studio
    - Canvas (canvasbase)
    - Canvas (canvasbase)
    - Common core services (ccs)


**Service**

**External
dependencies Service dependencies Component dependencies**
Voice Gateway None To install this service,
you must have the
following service
already installed:

```
None
```
Watson Discovery To install this service,
you must have
Multicloud Object
Gateway. For more
information, see
Installing and setting
up Multicloud Object
Gateway

```
None This service automatically installs
the following dependencies if they
are not already installed:
```
Watson Machine
Learning

```
None The following services
are not required but
provide additional
functionality:
```
```
The service automatically installs the
following dependencies if they are
not already installed:
```
Watson Machine
Learning
Accelerator

```
To install this service,
you must install the
following operators:
```
```
To install this service,
you must have the
following service
already installed:
```
```
The following services
are not required but
provide additional
functionality:
```
```
None
```
- watsonx Assistant
    Watson Speech to
    Text

### –

```
Watson Text to
Speech
```
### –

```
Cloud Native PostgreSQL
(postgresql)
```
### –

- etcd (opencontent_etcd)
    OpenSearch
    (opencontent_elasticsearch)

### –

- MinIO (opencontent_minio)
    RabbitMQ
    (opencontent_rabbitmq)

### –

```
Watson Gateway
(watson_gateway)
```
### –

```
Watson Machine
Learning Accelerator
provides the
Experiment Builder
user interface.
```
### –

- Common core services (ccs)
    OpenSearch
    (opencontent_elasticsearch)

### –

```
Node Feature
Discovery
Operator
Install the stable
version of the
operator.
```
### –

### NVIDIA GPU

```
Operator
```
### –

- Scheduling service

```
Watson Machine
Learning enables you
```
### –


**Service**

```
External
dependencies Service dependencies Component dependencies
```
Watson OpenScale If you prefer to
connect to an
external database,
you must have Db
Enterprise Server
Edition 11.5 or later.

```
If you want to connect
to an integrated
database, you must
have at least one
instance of a
supported, integrated
database:
```
```
The following services
are not required but
provide additional
functionality. To use the
functionality, you must
install the services
before you install
Watson OpenScale:
```
```
None
```
```
The version that
you install
depends on the
version of Red Hat
OpenShift
Container Platform
that you are
running:
On OpenShift
4.12, use
v23.9.x or
v24.3.x
```
### ▪

```
On OpenShift
4.14, use
v23.9.x or
v24.3.x
```
### ▪

```
On OpenShift
4.15, use
v24.3.x
```
### ▪

```
to use Deep Learning
Experiments
```
- Db
- Db2 Warehouse
- EDB Postgres

```
Watson Studio
enables you to:
```
### –

```
Create AutoAI
models and
Jupyter Notebooks
```
### ▪

```
▪ Set up a demo
```

**Service**

```
External
dependencies Service dependencies Component dependencies
```
Watson Speech
services

```
To install this service,
you must have
Multicloud Object
Gateway. For more
information, see
Installing and setting
up Multicloud Object
Gateway
```
```
None This service automatically installs
the following dependencies if they
are not already installed:
```
Watson Studio None The service
automatically installs
the following services if
they are not already
installed:

```
This service automatically installs
the following dependencies if they
are not already installed:
```
Watson Studio
Runtimes

```
The following
information applies
to GPU runtimes
only.
```
```
To install this service,
you must have the
following service
already installed:
```
```
None
```
watsonx.ai To install this service,
you must install the
following operators:

```
The service
automatically installs
the following services if
they are not already
```
```
This service automatically installs
the following dependencies if they
are not already installed:
```
```
environment
where you can
quickly tour the
Watson OpenScale
capabilities
Watson Machine
Learning enables you
to:
```
### –

```
Create a deployed
model that Watson
OpenScale can
check for bias and
drift
```
### ▪

```
Automatically log
payloads
```
### ▪

```
Cloud Native PostgreSQL
(postgresql)
```
### –

- MinIO (opencontent_minio)
    RabbitMQ
    (opencontent_rabbitmq)

### –

```
Watson Gateway
(watson_gateway)
```
### –

- Data Refinery
    Watson Studio
    Runtimes

### –

- Common core services (ccs)
    OpenSearch
    (opencontent_elasticsearch)

### –

- Watson Studio
- Node Feature –Common core services (ccs)


**Service**

```
External
dependencies Service dependencies Component dependencies
```
```
For more information
on installing these
operators, see
Installing operators
for services that
require GPUs.
```
```
installed:
```
```
The following services
are not required but
provide additional
functionality:
```
watsonx Assistant To install this service,
you must install the
following software
on the cluster:

```
If you plan to use
conversational search,
you must install Watson
Discovery or
Elasticsearch.
```
```
If you don't plan to use
conversational search,
the following services
```
```
This service automatically installs
the following dependencies if they
are not already installed:
```
```
Discovery
Operator
Install the stable
version of the
operator.
```
```
NVIDIA GPU
Operator
The version that
you install
depends on the
version of Red Hat
OpenShift
Container Platform
that you are
running:
```
### –

```
On OpenShift
4.12, use
v23.9.x or
v24.3.x
```
### ▪

```
On OpenShift
4.14, use
v23.9.x or
v24.3.x
```
### ▪

```
On OpenShift
4.15, use
v24.3.x
```
### ▪

```
Red Hat OpenShift
AI Operator
Version 2.8.
```
### –

- Watson Studio
    Watson Machine
    Learning

### –

```
watsonx.governance
enables you to
govern your
generative AI assets.
```
### –

```
Inference foundation models
(watsonx_ai_ifm)
```
### –

```
OpenSearch
(opencontent_elasticsearch)
```
### –

```
Multicloud Object
Gateway.
For more
information, see
```
### –

```
Cloud Native PostgreSQL
(postgresql)
```
### –

- etcd (opencontent_etcd)
    OpenSearch
    (opencontent_elasticsearch)

### –


**Service**

```
External
dependencies Service dependencies Component dependencies
```
```
If you plan to use
conversational skills
or conversational
search features, you
must install the
following operators:
```
```
are not required but
provide additional
functionality:
```
```
If you enable the GPU features
(conversational skills and
conversational search), the service
automatically installs the following
dependencies if they are not already
installed:
```
```
Installing and
setting up
Multicloud Object
Gateway
```
```
Red Hat OpenShift
Serverless Knative
Eventing
For more
information, see
Installing Red Hat
OpenShift
Serverless Knative
Eventing
```
### –

```
Node Feature
Discovery
Operator
Install the stable
version of the
operator.
```
### –

### NVIDIA GPU

```
Operator
The version that
you install
depends on the
version of Red Hat
OpenShift
Container Platform
that you are
running:
```
### –

```
On OpenShift
4.12, use
v23.9.x or
v24.3.x
```
### ▪

```
On OpenShift
4.14, use
v23.9.x or
v24.3.x
```
### ▪

```
Watson Discovery
enables you to add a
search skill to your
assistant.
```
### –

- MinIO (opencontent_minio)
- Redis (ibm_redis_cp)
    Watson data governor
    (data_governor)

### –

```
Watson Gateway
(watson_gateway)
```
### –

- Common core services (ccs)
    Inference foundation models
    (watsonx_ai_ifm)

### –

```
OpenSearch
(opencontent_elasticsearch)
```
### –


**Service**

```
External
dependencies Service dependencies Component dependencies
```
```
For more information
on installing these
operators, see
Installing operators
for services that
require GPUs.
```
watsonx Code
Assistant for Red
Hat Ansible®
Lightspeed

```
To install this service,
you must install the
following operators:
```
```
The service
automatically installs
the following services if
they are not already
installed:
```
```
This service automatically installs
the following dependencies if they
are not already installed:
```
```
On OpenShift
4.15, use
v24.3.x
```
### ▪

```
Red Hat OpenShift
AI Operator
Version 2.8.
```
### –

```
Node Feature
Discovery
Operator
Install the stable
version of the
operator.
```
### –

### NVIDIA GPU

```
Operator
The version that
you install
depends on the
version of Red Hat
OpenShift
Container Platform
that you are
running:
```
### –

```
On OpenShift
4.12, use
v23.9.x or
v24.3.x
```
### ▪

```
On OpenShift
4.14, use
v23.9.x or
v24.3.x
```
### ▪

```
On OpenShift
4.15, use
v24.3.x
```
### ▪

- Red Hat OpenShift
    - watsonx.ai
       - Common core services (ccs)
          Inference foundation models
          (watsonx_ai_ifm)

### –

```
OpenSearch
(opencontent_elasticsearch)
```
### –


**Service**

```
External
dependencies Service dependencies Component dependencies
```
```
For more information
on installing these
operators, see
Installing operators
for services that
require GPUs.
```
```
In addition, you must
have a Red Hat
Ansible Lightspeed
subscription. For
more information,
see Red Hat Ansible
Lightspeed with IBM
watsonx Code
Assistant.
```
watsonx Code
Assistant for Z

```
To install this service,
you must install the
following operators:
```
```
None This service automatically installs
the following dependencies if they
are not already installed:
```
```
AI Operator
Version 2.8.
```
```
Node Feature
Discovery
Operator
Install the stable
version of the
operator.
```
### –

### NVIDIA GPU

```
Operator
The version that
you install
depends on the
version of Red Hat
OpenShift
Container Platform
that you are
running:
```
### –

```
On OpenShift
4.12, use
v23.9.x or
v24.3.x
```
### ▪

```
On OpenShift
4.14, use
v23.9.x or
```
### ▪

- Common core services (ccs)
    Inference foundation models
    (watsonx_ai_ifm)

### –

```
OpenSearch
(opencontent_elasticsearch)
```
### –


**Service**

```
External
dependencies Service dependencies Component dependencies
```
```
For more information
on installing these
operators, see
Installing operators
for services that
require GPUs.
```
```
In addition you must
have an external Db
database.
```
```
End users must have
Visual Studio Code
on their
workstations. For
more information,
see Set up a
development
environment in the
IBM watsonx Code
Assistant for Z
documentation.
```
watsonx.data None The service
automatically installs
the following services if
they are not already
installed:

```
None
```
watsonx.governance To install this service,
you must install the
following operators:

```
The service
automatically installs
the following services if
they are not already
installed:
```
```
This service automatically installs
the following dependencies if they
are not already installed:
```
```
v24.3.x
On OpenShift
4.15, use
v24.3.x
```
### ▪

```
Red Hat OpenShift
AI Operator
Version 2.8.
```
### –

```
Analytics Engine
powered by Apache
Spark
```
### –

```
Red Hat OpenShift
AI Operator
Version 2.8.
```
### –

- Watson Machine
    - Common core services (ccs)
    - Db2 as a service (db2aaservice)
    - Db2U (db2u)
    - Inference foundation models


**Service**

```
External
dependencies Service dependencies Component dependencies
For more information
on installing these
operators, see
Installing operators
for services that
require GPUs.
```
```
If you want to connect
to an integrated
database for
watsonx.governance
Model Management,
you must have at least
one instance of a
supported, integrated
database:
```
```
The following services
are not required but
provide additional
functionality:
```
watsonx
Orchestrate

```
To install this service,
you must install the
following operators:
```
```
This service
automatically installs
the following service:
```
```
This service automatically installs
the following dependencies if they
are not already installed:
```
```
Learning
```
- Db2
- Db2 Warehouse
- EDB Postgres

```
Cognos Analytics
enables you to
generate reports and
create dashboards.
```
### –

```
watsonx.ai enables
you to build and
deploy generative AI
assets.
```
### –

```
(watsonx_ai_ifm)
OpenSearch
(opencontent_elasticsearch)
```
### –

```
RabbitMQ
(opencontent_rabbitmq)
```
### –

```
Node Feature
Discovery
Operator
Install the stable
version of the
operator.
```
### –

### NVIDIA GPU

```
Operator
The version that
you install
depends on the
version of Red Hat
OpenShift
```
### –

- watsonx Assistant Cloud Native PostgreSQL
    (postgresql)

### –

- Common core services (ccs)
- etcd (opencontent_etcd)
    Inference foundation models
    (watsonx_ai_ifm)

### –

- MinIO (opencontent_minio)
    MongoDB (both mongodb and
    mongodb_cp4d)

### –

```
OpenSearch
(opencontent_elasticsearch)
```
### –

```
RabbitMQ
(opencontent_rabbitmq)
```
### –

- Redis (ibm_redis_cp)


**Service**

```
External
dependencies Service dependencies Component dependencies
```
```
For more information
on installing these
operators, see
Installing operators
for services that
require GPUs.
```
```
To install this service,
you must install the
following software
on the cluster:
```
```
Container Platform
that you are
running:
On OpenShift
4.12, use
v23.9.x or
v24.3.x
```
### ▪

```
On OpenShift
4.14, use
v23.9.x or
v24.3.x
```
### ▪

```
On OpenShift
4.15, use
v24.3.x
```
### ▪

```
Red Hat OpenShift
AI Operator
Version 2.8.3
```
### –

```
Multicloud Object
Gateway.
For more
information, see
Installing and
setting up
Multicloud Object
Gateway
```
### –

```
Red Hat OpenShift
Serverless Knative
Eventing
For more
information, see
Installing Red Hat
OpenShift
Serverless Knative
```
### –

```
Watson data governor
(data_governor)
```
### –

```
Watson Gateway
(watson_gateway)
```
### –


## Supported web browsers

You can use the following web browsers to access the Cloud Pak for Data web client.

It is recommended that you use the latest available version or the latest version approved by your enterprise.

```
Parent topic:
System requirements
```
```
Service
```
```
External
dependencies Service dependencies Component dependencies
```
```
You can optionally
install IBM Robotic
Process Automation
if you want to run
Robotic Process
Automation bots as
skills in watsonx
Orchestrate. For
more information,
see Installing IBM
Robotic Process
Automation.
```
```
Eventing
```
```
IBM App Connect
in containers
For more
information, see
Installing IBM App
Connect in
containers.
```
### –

- Mozilla Firefox (recommended)
- Google Chrome
- Microsoft Edge


