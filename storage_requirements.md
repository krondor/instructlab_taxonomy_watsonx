# Storage requirements

Last Updated: 2024-06-

Before you install IBM Cloud Pak for Data, review the storage requirements for the control plane, the shared cluster components, and
the services that you plan to install.

## Cloud Pak for Data platform storage requirements

A Cloud Pak for Data deployment requires several types of storage:

**Storage for images in the private container registry**

```
Depending on your environment, you might need to store images in a private container registry rather than pulling them directly
from the IBM Entitled Registry.
If you use a private container registry, you must have sufficient space for the Cloud Pak for Data components that you plan to install.
```
```
Sizing
```
```
A minimum of 500 GB of storage space in the private container registry.
```
**Local storage for container images**

```
Each node on your cluster must have local storage for the container images that are running on that node.
```
```
Storage location
```
```
The container images are stored in the root file system on the nodes.
On Red Hat® OpenShift® Container Platform, local copies of the images are stored in /var/lib/containers. For details, see
Data storage management in the Red Hat OpenShift Container Platform documentation:
```
- Cloud Pak for Data platform storage requirements
- Cloud Pak for Data control plane persistent storage requirements
- Shared component persistent storage requirements
    ▪ Recommended storage classes for the shared components
- Service persistent storage requirements
    ▪ Recommended storage classes for services

```
Best practices:
Review the image size information in Hardware requirements to ensure that you have sufficient space for the images
you plan to mirror.
```
### –

```
Use the cpd-cli manage delete-images command to remove unused images from the private container
registry.
```
### –

- Version 4.
- Version 4.
- Version 4.


```
Sizing
```
```
A minimum of 500 GB of storage space per node.
```
**Persistent storage**

```
Cloud Pak for Data supports and is optimized for several types of persistent storage:
```
```
Storage option Version Notes
OpenShift Data Foundation Available in Red Hat OpenShift Platform
Plus.
Ensure that you install a version of
OpenShift Data Foundation that is
compatible with the version of Red Hat
OpenShift Container Platform that you
are running. For details, see https://
access.redhat.com/articles/4731161.
```
```
IBM Storage Fusion Data Foundation Available in IBM Storage Fusion.
Ensure that you install a version of IBM
Storage Fusion Data Foundation that is
compatible with the version of Red Hat
OpenShift Container Platform that you
are running.
```
```
If you are upgrading to IBM Cloud Pak
for Data Version 5.0, upgrade your
storage after you upgrade IBM Cloud Pak
for Data.
```
```
IBM Storage Fusion Global Data Platform Available in IBM Storage Fusion or IBM
Storage Fusion HCI System.
If you are upgrading to IBM Cloud Pak
for Data Version 5.0, upgrade your
storage after you upgrade IBM Cloud Pak
for Data.
```
```
IBM Storage Scale Container Native (with IBM
Storage Scale Container Storage Interface)
```
```
Version 5.1.7 or later
fixes, with CSI Version
2.9.0 or later fixes
```
```
Available in the following storage:
```
```
Portworx If you are running Red Hat OpenShift
Container Platform Version 4.12, you
must use Portworx Version 2.13.3 or
later.
If you are running Red Hat OpenShift
Container Platform Version 4.14, you
must use Portworx Version 3.0.2 or later.
```
```
NFS Version 3 or 4 Version 3 is recommended if you are
using any of the following services:
```
```
Version 4.12 or later
fixes
```
### –

```
Version 4.14 or later
fixes
```
### –

```
Version 4.15 or later
fixes
```
### –

```
Version 2.7.2 with the
latest hotfix or later
fixes
```
### –

```
Version 2.8.0 or later
fixes
```
### –

```
Version 2.7.2 with the
latest hotfix or later
fixes
```
### –

```
Version 2.8.0 or later
fixes
```
### –

- IBM Storage Fusion
- IBM Storage Suite for IBM Cloud Paks

```
Version 2.13.3 or later
fixes
```
### –

```
Version 3.0.2 or later
fixes
```
### –

- Data Product Hub
- Data Virtualization
- DataStage


```
When you plan your environment, ensure that you review the storage types that are supported by the components that you plan to
install:
```
```
Sizing
```
```
The minimum amount of storage depends on the type of storage that you plan to use. For details, see the Resource requirements
section under Storage comparison.
As a general rule, Cloud Pak for Data with all services installed can use up to 700 GB of storage space. Review the Storage
comparison to ensure that you have sufficient storage space available for user data based on the type of storage that you select.
You can add additional capacity depending on your user data volume requirements.
```
## Cloud Pak for Data control plane persistent storage requirements

The Cloud Pak for Data control plane supports all of the persistent storage options that are supported by the platform.

The control plane uses ReadWriteOnce (RWO) storage, which is specified through the --block_storage_class option. However, the
installation and upgrade commands include both of the following options:

The following table lists the recommended storage classes. If your cluster uses different storage class names, ensure that you specify
equivalent storage classes.

```
Storage option Version Notes
```
```
If you use Version 4, ensure that your
storage class uses NFS Version 3 as the
mount option. For details, see Setting up
dynamic provisioning.
```
```
Amazon Elastic Block Store (EBS) Not applicable In addition to EBS storage, your
environment must also include EFS
storage.
Amazon Elastic File System (EFS) Not applicable It is recommended that you use both
EBS and EFS storage.
NetApp Trident Version 23.07 or later
fixes
```
```
This information applies to both self-
managed and managed NetApp Trident.
```
- Db
- Db2 Big SQL
- Db2 Warehouse
- IBM Knowledge Catalog
- IBM Knowledge Catalog Premium
- IBM Knowledge Catalog Standard
- OpenPages
- Shared component persistent storage requirements
- Service persistent storage requirements

```
Tip: The preceding storage options have been evaluated by IBM. You can run the Cloud Pak for Datastorage validation tool
to assess storage that is provided by other vendors. However, this tool does not guarantee support for other types of
storage. You can use other storage environments at your own risk.
```
- --block_storage_class
- --file_storage_class


```
The --block_storage_class option should point to block storage or to a file storage class that supports ReadWriteOnce (RWO)
access.
```
### –

- The --file_storage_class option should point to a file storage class that supports ReadWriteMany (RWX) access.

```
Storage option Recommended block
storage class
```
```
Recommended file
storage class
```
```
Notes
```
```
OpenShift Data
Foundation
```
```
ocs-
storagecluster-
ceph-rbd
```
```
ocs-
storagecluster-
cephfs
```
```
The default storage class names are different if
you use external mode.
```
```
IBM Storage Fusion
Data Foundation
```
```
ocs-
storagecluster-
ceph-rbd
```
```
ocs-
storagecluster-
cephfs
```
```
The default storage class names are different if
you use external mode.
```
```
IBM Storage Fusion
Global Data Platform
```
```
Either of the following
storage classes:
```
```
Either of the following
storage classes:
```
```
IBM Storage Fusion Global Data Platform
supports both ReadWriteMany (RWX access) and
ReadWriteOnce (RWO access) with the same
storage class.
Specify the same storage class for block storage
and file storage.
```
```
IBM Storage Scale
Container Native
```
```
ibm-spectrum-
scale-sc
```
```
ibm-spectrum-
scale-sc
```
```
IBM Storage Scale Container Native supports
both ReadWriteMany (RWX access) and
ReadWriteOnce (RWO access) with the same
storage class.
Specify the same storage class for block storage
and file storage.
```
```
Portworx
```
```
portworx-
metastoredb-sc
```
```
portworx-rwx-
gp3-sc
```
```
For more information about the recommended
Portworx storage classes, see Creating Portworx
storage classes.
```
### NFS

```
managed-nfs-
storage
```
```
managed-nfs-
storage
```
```
NFS supports both ReadWriteMany (RWX access)
and ReadWriteOnce (RWO access) with the same
storage class.
Specify the same storage class for block storage
and file storage.
```
```
Amazon Elastic Block
Store
```
```
Either of the following
storage classes:
Not applicable.
```
```
Your environment must include Amazon Elastic
File System storage in addition to Amazon Elastic
Block Store.
```
```
Amazon Elastic File
System
```
```
Not applicable. efs-nfs-client
```
```
It is strongly recommended that you use both
Amazon Elastic Block Store storage and Amazon
Elastic File System storage.
```
```
If you use only Amazon Elastic File System,
specify efs-nfs-client for both file and block
storage.
```
```
ibm-spectrum-
scale-sc
```
### –

```
ibm-storage-
fusion-cp-sc
```
### –

```
ibm-spectrum-
scale-sc
```
### –

```
ibm-storage-
fusion-cp-sc
```
### –

- gp2-csi
- gp3-csi

```
The Cloud Pak for Data control plane is more
performant when you provide both file and
block storage.
```
### –

```
You can install services that require both file
and block storage.
```
### –


## Shared component persistent storage requirements

The following table indicates the type of storage that each component supports. For information about the recommended storage
classes for each component, see Recommended storage classes for the shared components.

In the following table, Data Foundation means either Red Hat OpenShift Data Foundation or IBM Storage Fusion Data Foundation.

## Recommended storage classes for the shared components

If you use different storage class names on your cluster, ensure that you specify equivalent storage classes.

▸ IBM Cloud Pak foundational services

▸ Common core services

## Service persistent storage requirements

The following table indicates the type of storage that each component supports. Additional information about the recommended
storage classes for each component are provided after the table.

```
Storage option
```
```
Recommended block
storage class
```
```
Recommended file
storage class Notes
```
```
NetApp Trident ontap-nas ontap-nas
```
```
NetApp Trident supports both ReadWriteMany
(RWX access) and ReadWriteOnce (RWO access)
with the same storage class.
Specify the same storage class for block storage
and file storage.
```
- **File req** indicates that a service can use the specified block storage only if file storage is also provided.
- **--** indicates that the service does not use persistent storage.

```
Component Data
Foundation
```
### IBM

```
Storage
Fusion
Global
Data
Platform
```
### IBM

```
Storage
Scale
Container
Native
```
```
Portworx NFS
```
```
Amazon
Elastic
Block
Store
```
```
Amazon
Elastic
File
System
```
```
NetApp
Trident
```
```
IBM Cloud
Pak
foundational
services
```
### ✓ ✓ ✓ ✓ ✓ ✓ ✓ ✓

```
scheduling
service
```
### -- -- -- -- -- -- -- --

```
Common
core
services
```
```
✓ ✓ ✓ ✓ ✓ File req ✓ ✓
```
```
Note: The scheduling service is not included in this list because it does not require persistent storage.
```
```
Combo pref indicates that a service can be installed with only the specified block storage but it is not recommended. A combination
of file storage and block storage is preferred.
```
### –


In the following table, Data Foundation means either Red Hat OpenShift Data Foundation or IBM Storage Fusion Data Foundation.

```
Block pref indicates that the service can be installed with either file storage or block storage but that block storage is preferred over
file storage.
```
### –

- **Block req** indicates that a service can use the specified file storage only if block storage is also provided.
- **File req** indicates that a service can use the specified block storage only if file storage is also provided.
- **CCS** indicates that the service uses the storage only to install the common core services.

```
Remember: Common core services require a combination of block and file storage.
```
- **Reuse** indicates that a service uses the storage that is provisioned by another service.

```
Component Data
Foundation
```
### IBM

```
Storage
Fusion
Global
Data
Platform
```
### IBM

```
Storage
Scale
Container
Native
```
```
Portworx NFS
```
```
Amazon
Elastic
Block
Store
```
```
Amazon
Elastic
File
System
```
```
NetApp
Trident
```
```
AI Factsheets CCS CCS CCS CCS CCS CCS CCS CCS
```
```
Anaconda
Repository for IBM
Cloud Pak for Data
```
### N/A N/A N/A N/A N/A N/A N/A N/A

```
Analytics Engine
powered by Apache
Spark
```
### ✓ ✓ ✓ ✓ ✓ ✓ ✓

```
Cognos Analytics ✓ ✓ ✓ ✓ ✓ File req
```
```
Block
req
```
### ✓

```
Cognos Dashboards ✓ ✓ ✓ ✓ ✓ CCS ✓ ✓
```
```
Data Gate ✓ ✓ ✓ ✓ ✓ ✓
```
```
Block
pref
```
### ✓

```
Data Privacy Reuse Reuse Reuse Reuse Reuse Reuse Reuse Reuse
```
```
Data Product Hub CCS CCS CCS CCS CCS CCS ✓CCS CCS
```
```
Data Refinery Reuse Reuse Reuse Reuse Reuse Reuse Reuse Reuse
```
```
Data Replication ✓ ✓ ✓ ✓ ✓ File req Block
req
```
### ✓

```
DataStage ✓ ✓ ✓ ✓ ✓ CCS ✓ ✓
```
```
Data Virtualization ✓ ✓ ✓ ✓ ✓ CCS ✓ ✓
```
```
Db2 ✓ ✓ ✓ ✓ ✓
```
```
Combo
pref
```
### ✓ ✓

```
Db2 Big SQL ✓ ✓ ✓ ✓ ✓ ✓ ✓
```
```
Component Data
Foundation
```
### IBM

```
Storage
Fusion
Global
Data
```
### IBM

```
Storage
Scale
Container
Native
```
```
Portworx NFS Amazon
Elastic
Block
Store
```
```
Amazon
Elastic
File
System
```
```
NetApp
Trident
```

**Component Data
Foundation**

### IBM

```
Storage
Fusion
Global
Data
Platform
```
### IBM

```
Storage
Scale
Container
Native
```
```
Portworx NFS
```
```
Amazon
Elastic
Block
Store
```
```
Amazon
Elastic
File
System
```
```
NetApp
Trident
```
```
Platform
```
Db2 Data
Management
Console

```
✓ ✓ ✓ ✓ ✓ File req ✓ ✓
```
Db2 Warehouse ✓ ✓ ✓ ✓ ✓ Combo
pref

### ✓ ✓

Decision
Optimization Reuse Reuse Reuse Reuse Reuse Reuse Reuse Reuse

EDB Postgres ✓ ✓ ✓ ✓ ✓

Execution Engine for
Apache Hadoop

### ✓ ✓ ✓ ✓ ✓ ✓ ✓

IBM Knowledge
Catalog ✓ ✓ ✓ ✓ ✓ File req ✓ ✓
IBM Knowledge
Catalog Premium ✓ ✓ ✓ ✓ ✓ File req ✓ ✓
IBM Knowledge
Catalog Standard

```
✓ ✓ ✓ ✓ ✓ File req ✓ ✓
```
IBM Match 360 with
Watson

```
✓ ✓ ✓ ✓ ✓ File req
```
```
Block
req
```
### ✓

Informix ✓ ✓ ✓ ✓ ✓ ✓ ✓

MANTA Automated
Data Lineage

```
✓ ✓ ✓ ✓ ✓ File req ✓ ✓
```
MongoDB ✓ ✓ ✓ ✓ ✓

OpenPages ✓ ✓ ✓ ✓ ✓ File req ✓ ✓

Orchestration
Pipelines

```
Reuse Reuse Reuse Reuse Reuse Reuse Reuse Reuse
```
Planning Analytics ✓ ✓ ✓ ✓ ✓ ✓ ✓ ✓

**Component**

```
Data
Foundation
```
### IBM

```
Storage
Fusion
Global
Data
Platform
```
### IBM

```
Storage
Scale
Container
Native
```
```
Portworx NFS
```
```
Amazon
Elastic
Block
Store
```
```
Amazon
Elastic
File
System
```
```
NetApp
Trident
```
Product Master ✓ ✓ ✓ ✓ ✓ File req

```
Block
req
```
### ✓

RStudio® Server
Runtimes

```
Reuse Reuse Reuse Reuse Reuse Reuse Reuse Reuse
```
SPSS Modeler Reuse Reuse Reuse Reuse Reuse Reuse Reuse Reuse

Synthetic Data
Generator

### CCS CCS CCS CCS CCS CCS CCS CCS


## Recommended storage classes for services

If you use different storage class names on your cluster, ensure that you specify equivalent storage classes.

▾ AI Factsheets
AI Factsheets uses the file storage and block storage that is provisioned for common core services.

```
Component Data
Foundation
```
### IBM

```
Storage
Fusion
Global
Data
Platform
```
### IBM

```
Storage
Scale
Container
Native
```
```
Portworx NFS
```
```
Amazon
Elastic
Block
Store
```
```
Amazon
Elastic
File
System
```
```
NetApp
Trident
```
```
Voice Gateway ✓ ✓ ✓ ✓
```
```
Watson Discovery ✓ ✓ ✓ ✓ File req
```
```
Block
req
```
### ✓

```
Watson Machine
Learning
```
```
✓ ✓ ✓ ✓ ✓ File req ✓ ✓
```
```
Watson Machine
Learning
Accelerator
```
### ✓ ✓ ✓ ✓ ✓ ✓ ✓

```
Watson OpenScale ✓ ✓ ✓ ✓ ✓ File req ✓ ✓
```
```
Component Data
Foundation
```
### IBM

```
Storage
Fusion
Global
Data
Platform
```
### IBM

```
Storage
Scale
Container
Native
```
```
Portworx NFS
```
```
Amazon
Elastic
Block
Store
```
```
Amazon
Elastic
File
System
```
```
NetApp
Trident
```
```
Watson Speech
services
```
```
✓ ✓ ✓ ✓ File req
```
```
Block
req
```
### ✓

```
Watson Studio ✓ ✓ ✓ ✓ ✓ CCS ✓ ✓
```
```
Watson Studio
Runtimes
```
```
Reuse Reuse Reuse Reuse Reuse Reuse Reuse Reuse
```
```
watsonx Assistant ✓ ✓ ✓ ✓ File req
```
```
Block
req
```
### ✓

```
watsonx.ai ✓ ✓ ✓ ✓ ✓ ✓
```
```
watsonx Code
Assistant for Red
Hat Ansible®
Lightspeed
```
```
✓ ✓ ✓ ✓ ✓ File req Block
req
```
### ✓

```
watsonx Code
Assistant for Z
```
```
✓ ✓ ✓ ✓ ✓ File req
```
```
Block
req
```
### ✓

```
watsonx.data ✓ ✓ ✓ ✓ ✓ ✓ ✓
```
```
watsonx.governance ✓ ✓ ✓ ✓ ✓ File req
```
```
Block
req ✓
watsonx
Orchestrate
```
### ✓ ✓


The following storage classes are recommended for common core services. You must specify information about the storage you want to
use when you install the service.

▾ Analytics Engine powered by Apache Spark
Analytics Engine powered by Apache Spark uses file storage.

```
Storage Notes Storage classes
OpenShift Data
Foundation
```
```
When you install the service, specify file storage
and block storage.
```
```
IBM Storage Fusion
Data Foundation
```
```
When you install the service, specify file storage
and block storage.
```
```
IBM Storage Fusion
Global Data Platform
```
```
When you install the service, specify the same
storage class for both file storage and block
storage.
```
```
IBM Storage Scale
Container Native
```
```
When you install the service, specify the same
storage class for both file storage and block
storage.
Portworx When you install the service, the --
storage_vendor=portworx option ensures
that the service uses the correct storage classes.
```
```
NFS When you install the service, specify the same
storage class for both file storage and block
storage.
Amazon Elastic
storage
```
```
When you install the service, you can specify:
```
```
File storage is provided by Amazon Elastic File
System. Block storage is provided by Amazon
Elastic Block Store.
```
```
NetApp Trident When you install the service, specify the same
storage class for both file storage and block
storage.
```
- **File storage:** ocs-storagecluster-cephfs
    **Block storage:** ocs-storagecluster-
    ceph-rbd

### –

- **File storage:** ocs-storagecluster-cephfs
    **Block storage:** ocs-storagecluster-
    ceph-rbd

### –

```
File storage:
Either of the following storage classes:
```
### –

```
▪ ibm-spectrum-scale-sc
▪ ibm-storage-fusion-cp-sc
Block storage:
Either of the following storage classes:
```
### –

```
▪ ibm-spectrum-scale-sc
▪ ibm-storage-fusion-cp-sc
```
- **File storage:** ibm-spectrum-scale-sc
- **Block storage:** ibm-spectrum-scale-sc

```
File storage: portworx-rwx-gp3-sc
(Equivalent to portworx-shared-gp3 in
older installations)
```
### –

- **Block storage:**
    ▪ portworx-couchdb-sc
    ▪ portworx-elastic-sc
    ▪ portworx-gp3-sc
- **File storage:** managed-nfs-storage
- **Block storage:** managed-nfs-storage
- File storage only
- File storage and block storage (recommended)
- **File storage:** efs-nfs-client
**Block storage:**
Either of the following storage classes:

### –

```
▪ gp2-csi
▪ gp3-csi
```
- **File storage:** ontap-nas
- **Block storage:** ontap-nas


The following storage classes are recommended for Analytics Engine powered by Apache Spark. You must specify information about
the storage you want to use when you provision an instance of Analytics Engine powered by Apache Spark.

▾ Cognos Analytics
Cognos Analytics uses file storage and block storage.

The following storage classes are recommended for Cognos Analytics. You must specify information about the storage you want to use
when you install the service.

* indicates that the storage class is used only if common core services needs to be installed.

```
Storage Notes Storage classes
OpenShift Data
Foundation
```
```
File storage: ocs-storagecluster-cephfs
```
```
IBM Storage Fusion
Data Foundation
```
```
File storage: ocs-storagecluster-cephfs
```
```
IBM Storage Fusion
Global Data Platform
```
```
File storage:
Either of the following storage classes:
```
```
IBM Storage Scale
Container Native
```
```
File storage: ibm-spectrum-scale-sc
```
```
Portworx File storage: portworx-rwx-gp3-sc
(Equivalent to portworx-shared-gp3 in older
installations)
```
```
NFS File storage: managed-nfs-storage
```
```
Amazon Elastic
storage
```
```
File storage is provided by Amazon Elastic File
System.
```
```
File storage: efs-nfs-client
```
```
NetApp Trident File storage: ontap-nas
```
- ibm-spectrum-scale-sc
- ibm-storage-fusion-cp-sc

```
Storage Notes Storage classes
OpenShift Data
Foundation
```
```
When you install the service, specify file storage
and block storage.
```
```
IBM Storage Fusion
Data Foundation
```
```
When you install the service, specify file storage
and block storage.
```
```
IBM Storage Fusion
Global Data Platform
```
```
When you install the service, specify the same
storage class for both file storage and block
storage.
```
- **File storage:** ocs-storagecluster-cephfs
    **Block storage:** ocs-storagecluster-
    ceph-rbd

### –

- **File storage:** ocs-storagecluster-cephfs
    **Block storage:** ocs-storagecluster-
    ceph-rbd

### –

```
File storage:
Either of the following storage classes:
```
### –

```
▪ ibm-spectrum-scale-sc
▪ ibm-storage-fusion-cp-sc
Block storage:
Either of the following storage classes:
```
### –

```
▪ ibm-spectrum-scale-sc
```

▾ Cognos Dashboards
Cognos Dashboards uses file storage. However, this service might install common core services, which requires both file storage and
block storage.

The following storage classes are recommended for Cognos Dashboards. You must specify information about the storage you want to
use when you install the service.

* indicates that the storage class is used only if common core services needs to be installed.

```
Storage Notes Storage classes
```
```
IBM Storage Scale
Container Native
```
```
When you install the service, specify the same
storage class for both file storage and block
storage.
Portworx When you install the service, the --
storage_vendor=portworx option ensures
that the service uses the correct storage classes.
```
```
NFS When you install the service, specify the same
storage class for both file storage and block
storage.
Amazon Elastic
storage
```
```
When you install the service, specify file storage
and block storage.
File storage is provided by Amazon Elastic File
System. Block storage is provided by Amazon
Elastic Block Store.
```
```
NetApp Trident When you install the service, specify the same
storage class for both file storage and block
storage.
```
```
▪ ibm-storage-fusion-cp-sc
```
- **File storage:** ibm-spectrum-scale-sc
- **Block storage:** ibm-spectrum-scale-sc

```
File storage: portworx-rwx-gp3-sc
(Equivalent to portworx-shared-gp3 in
older installations)
```
### –

- **Block storage:**
    ▪ portworx-couchdb-sc*
    ▪ portworx-elastic-sc*
    ▪ portworx-gp3-sc
- **File storage:** managed-nfs-storage
- **Block storage:** managed-nfs-storage
- **File storage:** efs-nfs-client
    **Block storage:**
    Either of the following storage classes:

### –

```
▪ gp2-csi
▪ gp3-csi
```
- **File storage:** ontap-nas
- **Block storage:** ontap-nas

```
Storage Notes Storage classes
OpenShift Data
Foundation
```
```
When you install the service, specify file storage
and block storage.
```
```
IBM Storage Fusion
Data Foundation
```
```
When you install the service, specify file storage
and block storage.
```
```
IBM Storage Fusion
Global Data Platform
```
```
When you install the service, specify the same
storage class for both file storage and block
storage.
```
- **File storage:** ocs-storagecluster-cephfs
    **Block storage:** ocs-storagecluster-
    ceph-rbd*

### –

- **File storage:** ocs-storagecluster-cephfs
    **Block storage:** ocs-storagecluster-
    ceph-rbd*

### –

```
File storage:
Either of the following storage classes:
```
### –

```
▪ ibm-spectrum-scale-sc
▪ ibm-storage-fusion-cp-sc
```

▾ Data Gate
Data Gate can use either file storage or block storage. However, in some environments, one type of storage is recommended over the
other.

The following storage classes are recommended for Data Gate. You must specify information about the storage you want to use when
you install the service.

```
Storage Notes Storage classes
```
```
IBM Storage Scale
Container Native
```
```
When you install the service, specify the same
storage class for both file storage and block
storage.
Portworx When you install the service, the --
storage_vendor=portworx option ensures
that the service uses the correct storage classes.
```
```
NFS When you install the service, specify the same
storage class for both file storage and block
storage.
Amazon Elastic
storage
```
```
When you install the service, specify file storage
and block storage.
File storage is provided by Amazon Elastic File
System. Block storage is provided by Amazon
Elastic Block Store.
```
```
NetApp Trident When you install the service, specify the same
storage class for both file storage and block
storage.
```
```
Block storage:
Either of the following storage classes:
```
### –

```
▪ ibm-spectrum-scale-sc*
▪ ibm-storage-fusion-cp-sc
```
- **File storage:** ibm-spectrum-scale-sc
- **Block storage:** ibm-spectrum-scale-sc*

```
File storage: portworx-rwx-gp3-sc
(Equivalent to portworx-shared-gp3 in
older installations)
```
### –

- **Block storage:**
    ▪ portworx-couchdb-sc*
    ▪ portworx-elastic-sc*
    ▪ portworx-gp3-sc*
- **File storage:** managed-nfs-storage
- **Block storage:** managed-nfs-storage*
- **File storage:** efs-nfs-client
    **Block storage:**
    Either of the following storage classes:

### –

```
▪ gp2-csi*
▪ gp3-csi*
```
- **File storage:** ontap-nas
- **Block storage:** ontap-nas*

```
Storage Notes Storage classes
OpenShift Data
Foundation
```
```
On OpenShift Data Foundation, Data Gate uses
file storage.
```
```
File storage: ocs-storagecluster-cephfs
```
```
IBM Storage Fusion
Data Foundation
```
```
On IBM Storage Fusion Data Foundation, Data
Gate uses file storage.
```
```
File storage: ocs-storagecluster-cephfs
```
```
IBM Storage Fusion
Global Data Platform
```
```
On IBM Storage Fusion Global Data Platform,
Data Gate uses ibm-spectrum-scale-sc to
provision storage with ReadWriteOnce access.
```
```
Block storage:
Either of the following storage classes:
```
- ibm-spectrum-scale-sc
- ibm-storage-fusion-cp-sc


▾ Data Privacy
Data Privacy leverages the storage that is provisioned when you install IBM Knowledge Catalog.

▾ Data Product Hub
Data Product Hub uses the file storage and block storage that is provisioned for common core services.

The following storage classes are recommended for common core services. You must specify information about the storage you want to
use when you install the service.

```
Storage Notes Storage classes
IBM Storage Scale
Container Native
```
```
On IBM Storage Scale Container Native, Data
Gate uses ibm-spectrum-scale-sc to
provision storage with ReadWriteOnce access.
```
```
Block storage: ibm-spectrum-scale-sc
```
```
Portworx On Portworx, Data Gate uses file storage. File storage: portworx-db2-rwx-sc
```
```
NFS On NFS, Data Gate uses managed-nfs-
storage to provision storage with
ReadWriteOnce access.
```
```
Block storage: managed-nfs-storage
```
```
Amazon Elastic
storage
```
```
On Amazon Elastic storage, block storage is
preferred.
File storage is provided by Amazon Elastic File
System. Block storage is provided by Amazon
Elastic Block Store.
```
```
NetApp Trident On NetApp Trident, Data Gate uses ontap-nas
to provision storage with ReadWriteOnce access.
```
```
Block storage: ontap-nas
```
- **File storage:** efs-nfs-client
    **Block storage:**
    Either of the following storage classes:

### –

```
▪ gp2-csi
▪ gp3-csi
```
```
Storage Notes Storage classes
OpenShift Data
Foundation
```
```
When you install the service, specify file storage
and block storage.
```
```
IBM Storage Fusion
Data Foundation
```
```
When you install the service, specify file storage
and block storage.
```
```
IBM Storage Fusion
Global Data Platform
```
```
When you install the service, specify the same
storage class for both file storage and block
storage.
```
```
IBM Storage Scale
Container Native
```
```
When you install the service, specify the same
storage class for both file storage and block
storage.
```
- **File storage:** ocs-storagecluster-cephfs
    **Block storage:** ocs-storagecluster-
    ceph-rbd

### –

- **File storage:** ocs-storagecluster-cephfs
    **Block storage:** ocs-storagecluster-
    ceph-rbd

### –

```
File storage:
Either of the following storage classes:
```
### –

```
▪ ibm-spectrum-scale-sc
▪ ibm-storage-fusion-cp-sc
Block storage:
Either of the following storage classes:
```
### –

```
▪ ibm-spectrum-scale-sc
▪ ibm-storage-fusion-cp-sc
```
- **File storage:** ibm-spectrum-scale-sc
- **Block storage:** ibm-spectrum-scale-sc


▾ Data Refinery
Data Refinery leverages the storage that is provisioned when you install IBM Knowledge Catalog or Watson Studio.

▾ Data Replication
Data Replication uses block storage. However, this service might install common core services, which requires both file storage and
block storage.

The following storage classes are recommended for Data Replication. You must specify information about the storage you want to use
when you install the service.

* indicates that the storage class is used only if common core services needs to be installed.

```
Storage Notes Storage classes
Portworx When you install the service, the --
storage_vendor=portworx option ensures
that the service uses the correct storage classes.
```
```
NFS When you install the service, specify the same
storage class for both file storage and block
storage.
Amazon Elastic
storage
```
```
When you install the service, you can specify:
```
```
File storage is provided by IBM Cloud File
Storage. Block storage is provided by IBM Cloud
Block Storage.
```
```
NetApp Trident When you install the service, specify the same
storage class for both file storage and block
storage.
```
```
File storage: portworx-rwx-gp3-sc
(Equivalent to portworx-shared-gp3 in
older installations)
```
### –

- **Block storage:**
    ▪ portworx-couchdb-sc
    ▪ portworx-elastic-sc
    ▪ portworx-gp3-sc
- **File storage:** managed-nfs-storage
- **Block storage:** managed-nfs-storage*
- File storage only
- File storage and block storage (recommended)
- **File storage:** efs-nfs-client
**Block storage:**
Either of the following storage classes:

### –

```
▪ gp2-csi
▪ gp3-csi
```
- **File storage:** ontap-nas
- **Block storage:** ontap-nas

```
Storage Notes Storage classes
OpenShift Data
Foundation
```
```
When you install the service, specify file storage
and block storage.
```
```
IBM Storage Fusion
Data Foundation
```
```
When you install the service, specify file storage
and block storage.
```
```
IBM Storage Fusion
Global Data Platform
```
```
When you install the service, specify the same
storage class for both file storage and block
storage.
```
```
File storage: ocs-storagecluster-cephfs
*
```
### –

```
Block storage: ocs-storagecluster-
ceph-rbd
```
### –

```
File storage: ocs-storagecluster-cephfs
*
```
### –

```
Block storage: ocs-storagecluster-
ceph-rbd
```
### –

```
File storage:
Either of the following storage classes:
```
### –

```
▪ ibm-spectrum-scale-sc*
```

▾ DataStage
DataStage uses file storage. However, this service might install common core services, which requires both file storage and block
storage.

The following storage classes are recommended for DataStage. You must specify information about the storage you want to use when
you install the service.

* indicates that the storage class is used only if common core services needs to be installed.

```
Storage Notes Storage classes
```
```
IBM Storage Scale
Container Native
```
```
When you install the service, specify the same
storage class for both file storage and block
storage.
Portworx When you install the service, the --
storage_vendor=portworx option ensures
that the service uses the correct storage classes.
```
```
NFS When you install the service, specify the same
storage class for both file storage and block
storage.
Amazon Elastic
storage
```
```
When you install the service, specify file storage
and block storage.
File storage is provided by Amazon Elastic File
System. Block storage is provided by Amazon
Elastic Block Store.
```
```
NetApp Trident When you install the service, specify the same
storage class for both file storage and block
storage.
```
```
▪ ibm-storage-fusion-cp-sc
Block storage:
Either of the following storage classes:
```
### –

```
▪ ibm-spectrum-scale-sc
▪ ibm-storage-fusion-cp-sc
```
- **File storage:** ibm-spectrum-scale-sc*
- **Block storage:** ibm-spectrum-scale-sc

```
File storage: portworx-rwx-gp3-sc*
(Equivalent to portworx-shared-gp3 in
older installations)
```
### –

- **Block storage:**
    ▪ portworx-couchdb-sc*
    ▪ portworx-elastic-sc*
    ▪ portworx-gp3-sc
- **File storage:** managed-nfs-storage*
- **Block storage:** managed-nfs-storage
- **File storage:** efs-nfs-client
    **Block storage:**
    Either of the following storage classes:

### –

```
▪ gp2-csi*
▪ gp3-csi*
```
- **File storage:** ontap-nas*
- **Block storage:** ontap-nas

```
Storage Notes Storage classes
OpenShift Data
Foundation
```
```
When you install the service, specify file storage
and block storage.
```
```
IBM Storage Fusion
Data Foundation
```
```
When you install the service, specify file storage
and block storage.
```
- **File storage:** ocs-storagecluster-cephfs
    **Block storage:** ocs-storagecluster-
    ceph-rbd*

### –

- **File storage:** ocs-storagecluster-cephfs
    **Block storage:** ocs-storagecluster-
    ceph-rbd*

### –


▾ Data Virtualization

**Storage used during installation**

```
If the common core services are not installed, you must specify storage when you install Data Virtualization
```
```
Storage Notes Storage classes
IBM Storage Fusion
Global Data Platform
```
```
When you install the service, specify the same
storage class for both file storage and block
storage.
```
```
IBM Storage Scale
Container Native
```
```
When you install the service, specify the same
storage class for both file storage and block
storage.
Portworx When you install the service, the --
storage_vendor=portworx option ensures
that the service uses the correct storage classes.
```
```
NFS When you install the service, specify the same
storage class for both file storage and block
storage.
Amazon Elastic
storage
```
```
When you install the service, you can specify:
```
```
File storage is provided by Amazon Elastic File
System. Block storage is provided by Amazon
Elastic Block Store.
```
```
NetApp Trident When you install the service, specify the same
storage class for both file storage and block
storage.
```
```
File storage:
Either of the following storage classes:
```
### –

```
▪ ibm-spectrum-scale-sc
▪ ibm-storage-fusion-cp-sc
Block storage:
Either of the following storage classes:
```
### –

```
▪ ibm-spectrum-scale-sc*
▪ ibm-storage-fusion-cp-sc
```
- **File storage:** ibm-spectrum-scale-sc
- **Block storage:** ibm-spectrum-scale-sc*

```
File storage: portworx-rwx-gp3-sc
(Equivalent to portworx-shared-gp3 in
older installations)
```
### –

- **Block storage:**
    ▪ portworx-couchdb-sc*
    ▪ portworx-elastic-sc*
    ▪ portworx-gp3-sc*
- **File storage:** managed-nfs-storage
- **Block storage:** managed-nfs-storage*
- File storage only
- File storage and block storage (recommended)
- **File storage:** efs-nfs-client
**Block storage:**
Either of the following storage classes:

### –

```
▪ gp2-csi*
▪ gp3-csi*
```
- **File storage:** ontap-nas
- **Block storage:** ontap-nas*

```
Storage Notes Storage classes
OpenShift Data
Foundation
```
```
File storage: ocs-storagecluster-
cephfs
```
### –

```
Block storage: ocs-storagecluster-
ceph-rbd
```
### –


**Storage used during service instance provisioning**

```
Data Virtualization service instances use file and block storage.
```
```
The following storage classes are recommended for Data Virtualization. You must specify information about the storage you want to
```
```
Storage Notes Storage classes
IBM Storage Fusion
Data Foundation
```
```
IBM Storage Fusion
Global Data Platform
```
```
IBM Storage Fusion Global Data Platform
supports both ReadWriteMany (RWX access)
and ReadWriteOnce (RWO access) with the
same storage class.
```
```
IBM Storage Scale
Container Native
```
```
IBM Storage Scale Container Native supports
both ReadWriteMany (RWX access) and
ReadWriteOnce (RWO access) with the same
storage class.
Portworx
```
```
NFS NFS supports both ReadWriteMany (RWX
access) and ReadWriteOnce (RWO access) with
the same storage class.
Amazon Elastic
storage
```
```
On Amazon Elastic storage, this service can use
either:
```
```
File storage is provided by Amazon Elastic File
System. Block storage is provided by Amazon
Elastic Block Store.
```
```
NetApp Trident NetApp Trident supports both ReadWriteMany
(RWX access) and ReadWriteOnce (RWO
access) with the same storage class.
```
```
File storage: ocs-storagecluster-
cephfs
```
### –

```
Block storage: ocs-storagecluster-
ceph-rbd
```
### –

```
File storage:
Either of the following storage classes:
```
### –

```
▪ ibm-spectrum-scale-sc
▪ ibm-storage-fusion-cp-sc
Block storage:
Either of the following storage classes:
```
### –

```
▪ ibm-spectrum-scale-sc
▪ ibm-storage-fusion-cp-sc
```
- **File storage:** ibm-spectrum-scale-sc
- **Block storage:** ibm-spectrum-scale-sc
- **File storage:**
    portworx-rwx-gp3-sc
    (Equivalent to portworx-shared-gp3 in
    older installations)

### ▪

- **Block storage:**
    ▪ portworx-couchdb-sc
    ▪ portworx-elastic-sc
    ▪ portworx-gp3-sc
- **File storage:** managed-nfs-storage
- **Block storage:** managed-nfs-storage
- File storage only
File storage and block storage
(recommended)

### –

- **File storage:** efs-nfs-client
    **Block storage:**
    Either of the following storage classes:

### –

```
▪ gp2-csi
▪ gp3-csi
```
- **File storage:** ontap-nas
- **Block storage:** ontap-nas


use when you provision the Data Virtualization instance.

```
Storage Notes Storage classes
OpenShift Data
Foundation
```
```
When you create the service instance, specify
file storage and block storage.
```
```
IBM Storage Fusion
Data Foundation
```
```
When you create the service instance, specify
file storage and block storage.
```
```
IBM Storage Fusion
Global Data Platform
```
```
When you create the service instance, specify
the same storage class for both file storage and
block storage.
```
```
IBM Storage Scale
Container Native
```
```
When you create the service instance, specify
the same storage class for both file storage and
block storage.
Portworx When you create the service instance, specify
file storage and block storage.
```
```
NFS When you create the service instance, specify
the same storage class for both file storage and
block storage.
Amazon Elastic
storage
```
```
On Amazon Elastic storage, Data Virtualization
uses file storage.
File storage is provided by Amazon Elastic File
System.
```
```
Block storage, provided by Amazon Elastic
Block Store, is not supported.
```
```
File storage: efs-nfs-client
```
```
NetApp Trident When you create the service instance, specify
the same storage class for both file storage and
block storage.
```
```
Use ocs-storagecluster-cephfs for
audit storage.
```
### –

```
Use ocs-storagecluster-ceph-rbd for
node and caching storage.
```
### –

```
File storage: ocs-storagecluster-
cephfs
```
### –

```
Block storage: ocs-storagecluster-
ceph-rbd
```
### –

```
Use ocs-storagecluster-cephfs for
audit storage.
```
### –

```
Use ocs-storagecluster-ceph-rbd for
node and caching storage.
```
### –

```
File storage: ocs-storagecluster-
cephfs
```
### –

```
Block storage: ocs-storagecluster-
ceph-rbd
```
### –

```
File storage:
Either of the following storage classes:
```
### –

```
▪ ibm-spectrum-scale-sc
▪ ibm-storage-fusion-cp-sc
Block storage:
Either of the following storage classes:
```
### –

```
▪ ibm-spectrum-scale-sc
▪ ibm-storage-fusion-cp-sc
```
- **File storage:** ibm-spectrum-scale-sc
- **Block storage:** ibm-spectrum-scale-sc

```
Use portworx-db2-rwx-sc for caching and
audit storage.
```
### –

```
Use portworx-db2-rwo-sc for node
storage.
```
### –

- **File storage:** portworx-db2-rwx-sc
- **Block storage:** portworx-db2-rwo-sc
- **File storage:** managed-nfs-storage
- **Block storage:** managed-nfs-storage
- **File storage:** ontap-nas
- **Block storage:** ontap-nas


▾ Db
Db2 uses file storage and block storage on most storage environments.

The following storage classes are recommended for Db2. You must specify information about the storage you want to use when you
provision an instance of Db2.

```
Storage Notes Storage classes
OpenShift Data
Foundation
```
```
IBM Storage Fusion
Data Foundation
```
```
IBM Storage Fusion
Global Data Platform
```
```
Use ibm-spectrum-scale-sc for all data.
```
```
IBM Storage Scale
Container Native
```
```
Use ibm-spectrum-scale-sc for all data.
```
```
Portworx
```
```
Use ocs-storagecluster-cephfs for
system data and backup data.
```
### –

```
Use ocs-storagecluster-ceph-rbd for
user data, archive logs transaction logs, and
table space data.
Ensure that you select the 4K sector size
option in the web client or specify
DB2_4K_DEVICE_SUPPORT: "ON" in the
instance custom resource.
```
### –

- **File storage:** ocs-storagecluster-cephfs
    **Block storage:** ocs-storagecluster-
    ceph-rbd

### –

```
Use ocs-storagecluster-cephfs for
system data and backup data.
```
### –

```
Use ocs-storagecluster-ceph-rbd for
user data, archive logs transaction logs, and
table space data.
Ensure that you select the 4K sector size
option in the web client or specify
DB2_4K_DEVICE_SUPPORT: "ON" in the
instance custom resource.
```
### –

- **File storage:** ocs-storagecluster-cephfs
    **Block storage:** ocs-storagecluster-
    ceph-rbd

### –

```
File storage:
Either of the following storage classes:
```
### –

```
▪ ibm-spectrum-scale-sc
▪ ibm-storage-fusion-cp-sc
Block storage:
Either of the following storage classes:
```
### –

```
▪ ibm-spectrum-scale-sc
▪ ibm-storage-fusion-cp-sc
```
- **File storage:** ibm-spectrum-scale-sc
- **Block storage:** ibm-spectrum-scale-sc

```
Use portworx-db2-rwx-sc for system data
and backup data.
```
### –

```
Use portworx-db2-rwo-sc for user data,
archive logs transaction logs, and table space
data.
Ensure that you select the 4K sector size
option in the web client or specify
DB2_4K_DEVICE_SUPPORT: "ON" in the
instance custom resource.
```
### –

- **File storage:** portworx-db2-rwx-sc
- **Block storage:** portworx-db2-rwo-sc


▾ Db2 Big SQL
Db2 Big SQL uses block storage on most storage environments.

The following storage classes are recommended for Db2 Big SQL. You must specify information about the storage you want to use
when you provision the Db2 Big SQL instance.

```
Storage Notes Storage classes
NFS Use managed-nfs-storage for all data.
```
```
Amazon Elastic
storage
```
```
When you deploy the service you can specify:
```
```
If you use both file and block storage:
```
```
File storage is provided by Amazon Elastic File
System. Block storage is provided by Amazon
Elastic Block Store.
```
```
NetApp Trident Use ontap-nas for all data.
```
- **File storage:** managed-nfs-storage
- **Block storage:** managed-nfs-storage
- Block storage only
- File storage and block storage (recommended)

```
Use efs-nfs-client for system data and
backup data.
```
### –

```
Use gp2-csi or gp3-csi for user data,
archive logs transaction logs, and table space
data.
```
### –

- **File storage:** efs-nfs-client
    **Block storage:**
    Either of the following storage classes:

### –

```
▪ gp2-csi
▪ gp3-csi
```
- **File storage:** ontap-nas
- **Block storage:** ontap-nas

```
Storage Notes Storage classes
OpenShift Data
Foundation
```
```
Block storage: ocs-storagecluster-ceph-
rbd
IBM Storage Fusion
Data Foundation
```
```
Block storage: ocs-storagecluster-ceph-
rbd
IBM Storage Fusion
Global Data Platform
```
```
Block storage:
Either of the following storage classes:
```
```
IBM Storage Scale
Container Native
```
```
Block storage: ibm-spectrum-scale-sc
```
```
Portworx Block storage: portworx-db2-rwx-sc
```
```
NFS Block storage: managed-nfs-storage
```
```
Amazon Elastic
storage
```
```
File storage is provided by Amazon Elastic File
System.
Block storage, provided by Amazon Elastic Block
Store, is not supported.
```
```
File storage: efs-nfs-client
```
- ibm-spectrum-scale-sc
- ibm-storage-fusion-cp-sc


▾ Db2 Data Management Console
Db2 Data Management Console uses file storage or file storage and block storage.

The following storage classes are recommended for Db2 Data Management Console. You must specify information about the storage
you want to use when you provision the Db2 Data Management Console instance.

```
Storage Notes Storage classes
NetApp Trident Block storage: ontap-nas
```
```
Storage Notes Storage classes
OpenShift Data
Foundation
```
```
IBM Storage Fusion
Data Foundation
```
```
If you provision a Db2 Data Management
Console service instance from the UI, you must
specify file storage.
```
### –

```
If you provision a Db2 Data Management
Console by creating a custom resource, you
can specify:
```
### –

```
File storage only
Use the storageClass parameter.
```
### ▪

```
File storage and block storage
(recommended)
Use the fileStorageClass and
blockStorageClass parameters.
```
### ▪

- **File storage:** ocs-storagecluster-cephfs
    **Block storage:** ocs-storagecluster-
    ceph-rbd

### –

```
If you provision a Db2 Data Management
Console service instance from the UI, you must
specify file storage.
```
### –

```
If you provision a Db2 Data Management
Console by creating a custom resource, you
can specify:
```
### –

```
File storage only
Use the storageClass parameter.
```
### ▪

```
File storage and block storage
(recommended)
Use the fileStorageClass and
blockStorageClass parameters.
```
### ▪

- **File storage:** ocs-storagecluster-cephfs
    **Block storage:** ocs-storagecluster-
    ceph-rbd

### –


**Storage Notes Storage classes**
IBM Storage Fusion
Global Data Platform

IBM Storage Scale
Container Native

Portworx

### NFS

```
If you provision Db2 Data Management
Console service instance from the UI, ibm-
spectrum-scale-sc is used as file storage.
```
### –

```
If you provision a Db2 Data Management
Console by creating a custom resource, you
can specify:
```
### –

```
File storage only
Use the storageClass parameter.
```
### ▪

```
File storage and block storage
(recommended)
Use the fileStorageClass and
blockStorageClass parameters.
```
### ▪

```
File storage:
Either of the following storage classes:
```
### –

```
▪ ibm-spectrum-scale-sc
▪ ibm-storage-fusion-cp-sc
Block storage:
Either of the following storage classes:
```
### –

```
▪ ibm-spectrum-scale-sc
▪ ibm-storage-fusion-cp-sc
```
```
If you provision Db2 Data Management
Console service instance from the UI, ibm-
spectrum-scale-sc is used as file storage.
```
### –

```
If you provision a Db2 Data Management
Console by creating a custom resource, you
can specify:
```
### –

```
File storage only
Use the storageClass parameter.
```
### ▪

```
File storage and block storage
(recommended)
Use the fileStorageClass and
blockStorageClass parameters.
```
### ▪

- **File storage:** ibm-spectrum-scale-sc
- **Block storage:** ibm-spectrum-scale-sc

```
If you provision a Db2 Data Management
Console service instance from the UI, you must
specify file storage.
```
### –

```
If you provision a Db2 Data Management
Console by creating a custom resource, you
can specify:
```
### –

```
File storage only
Use the storageClass parameter.
```
### ▪

```
File storage and block storage
(recommended)
Use the fileStorageClass and
blockStorageClass parameters.
```
### ▪

```
File storage: portworx-rwx-gp3-sc
(Equivalent to portworx-shared-gp3 in
older installations)
```
### –

- **Block storage:** portworx-db-gp3-sc

```
If you provision Db2 Data Management
Console service instance from the UI,
managed-nfs-storage is used as file
storage.
```
### –

```
If you provision a Db2 Data Management
Console by creating a custom resource, you
can specify:
```
### –

```
File storage only
Use the storageClass parameter.
```
### ▪

```
▪ File storage and block storage
```
- **File storage:** managed-nfs-storage
- **Block storage:** managed-nfs-storage


▾ Db2 Warehouse
Db2 Warehouse uses file storage and block storage.

The following storage classes are recommended for Db2 Warehouse. You must specify information about the storage you want to use
when you provision an instance of Db2 Warehouse.

```
Storage Notes Storage classes
```
```
Amazon Elastic
storage
```
```
File storage is provided by Amazon Elastic File
System. Block storage is provided by Amazon
Elastic Block Store.
```
```
NetApp Trident
```
```
(recommended)
Use the fileStorageClass and
blockStorageClass parameters.
```
```
If you provision a Db2 Data Management
Console service instance from the UI, you must
specify file storage.
```
### –

```
If you provision a Db2 Data Management
Console by creating a custom resource, you
can specify:
```
### –

```
File storage only
Use the storageClass parameter.
```
### ▪

```
File storage and block storage
(recommended)
Use the fileStorageClass and
blockStorageClass parameters.
```
### ▪

- **File storage:** efs-nfs-client
    **Block storage:**
    Either of the following storage classes:

### –

```
▪ gp2-csi
▪ gp3-csi
```
```
If you provision Db2 Data Management
Console service instance from the UI, ontap-
nas is used as file storage.
```
### –

```
If you provision a Db2 Data Management
Console by creating a custom resource, you
can specify:
```
### –

```
File storage only
Use the storageClass parameter.
```
### ▪

```
File storage and block storage
(recommended)
Use the fileStorageClass and
blockStorageClass parameters.
```
### ▪

- **File storage:** ontap-nas
- **Block storage:** ontap-nas

```
Storage Notes Storage classes
OpenShift Data
Foundation
```
```
Use ocs-storagecluster-cephfs for
system data and backup data.
```
### –

```
Use ocs-storagecluster-ceph-rbd for
user data, archive logs transaction logs, and
table space data.
Ensure that you select the 4K sector size
option in the web client or specify
```
### –

- **File storage:** ocs-storagecluster-cephfs
    **Block storage:** ocs-storagecluster-
    ceph-rbd

### –


**Storage Notes Storage classes**

IBM Storage Fusion
Data Foundation

IBM Storage Fusion
Global Data Platform

```
Use ibm-spectrum-scale-sc for all data.
```
IBM Storage Scale
Container Native

```
Use ibm-spectrum-scale-sc for all data.
```
Portworx

NFS Use managed-nfs-storage for all data.

Amazon Elastic
storage

```
When you deploy the service you can specify:
```
```
If you use both file and block storage:
```
```
File storage is provided by Amazon Elastic File
```
```
DB2_4K_DEVICE_SUPPORT: "ON" in the
instance custom resource.
```
```
Use ocs-storagecluster-cephfs for
system data and backup data.
```
### –

```
Use ocs-storagecluster-ceph-rbd for
user data, archive logs transaction logs, and
table space data.
Ensure that you select the 4K sector size
option in the web client or specify
DB2_4K_DEVICE_SUPPORT: "ON" in the
instance custom resource.
```
### –

- **File storage:** ocs-storagecluster-cephfs
    **Block storage:** ocs-storagecluster-
    ceph-rbd

### –

```
File storage:
Either of the following storage classes:
```
### –

```
▪ ibm-spectrum-scale-sc
▪ ibm-storage-fusion-cp-sc
Block storage:
Either of the following storage classes:
```
### –

```
▪ ibm-spectrum-scale-sc
▪ ibm-storage-fusion-cp-sc
```
- **File storage:** ibm-spectrum-scale-sc
- **Block storage:** ibm-spectrum-scale-sc

```
Use portworx-db2-rwx-sc for system data
and backup data.
```
### –

```
Use portworx-db2-rwo-sc for user data,
archive logs transaction logs, and table space
data.
Ensure that you select the 4K sector size
option in the web client or specify
DB2_4K_DEVICE_SUPPORT: "ON" in the
instance custom resource.
```
### –

- **File storage:** portworx-db2-rwx-sc
- **Block storage:** portworx-db2-rwo-sc
- **File storage:** managed-nfs-storage
- **Block storage:** managed-nfs-storage
- Block storage only
- File storage and block storage (recommended)

```
Use efs-nfs-client for system data and
backup data.
```
### –

```
Use gp2-csi or gp3-csi for user data,
archive logs transaction logs, and table space
data.
```
### –

- **File storage:** efs-nfs-client
    **Block storage:**
    Either of the following storage classes:

### –

```
▪ gp2-csi
▪ gp3-csi
```

▾ Decision Optimization

Decision Optimization leverages the storage that is provisioned when you install Watson Studio.

▾ EDB Postgres
EDB Postgres uses block storage.

The following storage classes are recommended for EDB Postgres. You must specify information about the storage you want to use
when you provision an instance of EDB Postgres.

```
Storage Notes Storage classes
System. Block storage is provided by Amazon
Elastic Block Store.
```
```
NetApp Trident Use ontap-nas for all data. – File storage: ontap-nas
```
- **Block storage:** ontap-nas

```
Storage Notes Storage classes
OpenShift Data
Foundation
```
```
Block storage: ocs-storagecluster-ceph-
rbd
IBM Storage Fusion
Data Foundation
```
```
Block storage: ocs-storagecluster-ceph-
rbd
IBM Storage Fusion
Global Data Platform
```
```
Block storage:
Either of the following storage classes:
```
```
IBM Storage Scale
Container Native
```
```
Block storage: ibm-spectrum-scale-sc
```
```
Portworx Block storage: portworx-db-gp
```
```
NFS Not supported. Not applicable.
```
```
Amazon Elastic
storage
```
```
Block storage is provided by Amazon Elastic
Block Store.
```
```
Block storage:
Either of the following storage classes:
```
```
NetApp Trident Not supported. Not applicable.
```
- ibm-spectrum-scale-sc
- ibm-storage-fusion-cp-sc
- gp2-csi
- gp3-csi

```
Restriction: This service does not support the backup and restore methods provided by the underlying storage. For example,
```
```
For information on backing up this service, see Services that support backup and restore.
```
```
If you use IBM Storage Fusion Data Foundation or IBM Storage Fusion Global Data Platform for storage, the service cannot
use IBM Spectrum Protect Plus for backups.
```
### –

- If you use Portworx for storage, the service cannot use PX-Backup for backups


▾ Execution Engine for Apache Hadoop
Execution Engine for Apache Hadoop uses file storage.

The following storage classes are recommended for Execution Engine for Apache Hadoop. You must specify information about the
storage you want to use when you install the service.

▾ IBM Knowledge Catalog
IBM Knowledge Catalog uses file storage and block storage.

The following storage classes are recommended for IBM Knowledge Catalog. You must specify information about the storage you want
to use when you install the service.

```
Storage Notes Storage classes
OpenShift Data
Foundation
```
```
When you install the service, specify file storage.
If you specify block storage, the service ignores
this information.
```
```
File storage: ocs-storagecluster-cephfs
```
```
IBM Storage Fusion
Data Foundation
```
```
When you install the service, specify file storage.
If you specify block storage, the service ignores
this information.
```
```
File storage: ocs-storagecluster-cephfs
```
```
IBM Storage Fusion
Global Data Platform
```
```
When you install the service, specify file storage.
If you specify block storage, the service ignores
this information.
```
```
File storage:
Either of the following storage classes:
```
```
IBM Storage Scale
Container Native
```
```
When you install the service, specify file storage.
If you specify block storage, the service ignores
this information.
```
```
File storage: ibm-spectrum-scale-sc
```
```
Portworx When you install the service, the --
storage_vendor=portworx option ensures
that the service uses the correct storage classes.
```
```
File storage: portworx-rwx-gp3-sc
(Equivalent to portworx-shared-gp3 in older
installations)
```
```
NFS When you install the service, specify file storage.
If you specify block storage, the service ignores
this information.
```
```
File storage: managed-nfs-storage
```
```
Amazon Elastic
storage
```
```
When you install the service, specify file storage.
If you specify block storage, the service ignores
this information.
File storage is provided by Amazon Elastic File
System.
```
```
File storage: efs-nfs-client
```
```
NetApp Trident When you install the service, specify file storage.
If you specify block storage, the service ignores
this information.
```
```
File storage: ontap-nas
```
- ibm-spectrum-scale-sc
- ibm-storage-fusion-cp-sc

```
Storage Notes Storage classes
OpenShift Data
Foundation
```
```
When you install the service, specify file storage
and block storage.
```
```
IBM Storage Fusion
Data Foundation
```
```
When you install the service, specify file storage
and block storage.
```
- **File storage:** ocs-storagecluster-cephfs
    **Block storage:** ocs-storagecluster-
    ceph-rbd

### –

- **File storage:** ocs-storagecluster-cephfs
- **Block storage:** ocs-storagecluster-


▾ IBM Knowledge Catalog Premium
IBM Knowledge Catalog Premium uses file storage and block storage.

The following storage classes are recommended for IBM Knowledge Catalog Premium. You must specify information about the storage
you want to use when you install the service.

```
Storage Notes Storage classes
```
```
IBM Storage Fusion
Global Data Platform
```
```
When you install the service, specify the same
storage class for both file storage and block
storage.
```
```
IBM Storage Scale
Container Native
```
```
When you install the service, specify the same
storage class for both file storage and block
storage.
Portworx When you install the service, the --
storage_vendor=portworx option ensures
that the service uses the correct storage classes.
```
```
NFS When you install the service, specify the same
storage class for both file storage and block
storage.
Amazon Elastic
storage
```
```
When you install the service, you can specify:
```
```
File storage is provided by Amazon Elastic File
System. Block storage is provided by Amazon
Elastic Block Store.
```
```
NetApp Trident When you install the service, specify the same
storage class for both file storage and block
storage.
```
```
ceph-rbd
```
```
File storage:
Either of the following storage classes:
```
### –

```
▪ ibm-spectrum-scale-sc
▪ ibm-storage-fusion-cp-sc
Block storage:
Either of the following storage classes:
```
### –

```
▪ ibm-spectrum-scale-sc
▪ ibm-storage-fusion-cp-sc
```
- **File storage:** ibm-spectrum-scale-sc
- **Block storage:** ibm-spectrum-scale-sc
- **File storage:** portworx-shared-gp3
- **Block storage:**
    ▪ portworx-cassandra-sc
    ▪ portworx-couchdb-sc
    ▪ portworx-db2-rwo-sc
    ▪ portworx-elastic-sc
    ▪ portworx-gp3-sc
    ▪ portworx-kafka-sc
    ▪ portworx-metastoredb-sc
    ▪ portworx-solr-sc
- **File storage:** managed-nfs-storage
- **Block storage:** managed-nfs-storage
- File storage only
- File storage and block storage (recommended)
- **File storage:** efs-nfs-client
**Block storage:**
Either of the following storage classes:

### –

```
▪ gp2-csi
▪ gp3-csi
```
- **File storage:** ontap-nas
- **Block storage:** ontap-nas

```
Storage Notes Storage classes
OpenShift Data
Foundation
```
```
When you install the service, specify file storage
and block storage.
```
- **File storage:** ocs-storagecluster-cephfs
- **Block storage:** ocs-storagecluster-


▾ IBM Knowledge Catalog Standard
IBM Knowledge Catalog Standard uses file storage and block storage.

The following storage classes are recommended for IBM Knowledge Catalog Standard. You must specify information about the storage
you want to use when you install the service.

```
Storage Notes Storage classes
```
```
IBM Storage Fusion
Data Foundation
```
```
When you install the service, specify file storage
and block storage.
```
```
IBM Storage Fusion
Global Data Platform
```
```
When you install the service, specify the same
storage class for both file storage and block
storage.
```
```
IBM Storage Scale
Container Native
```
```
When you install the service, specify the same
storage class for both file storage and block
storage.
Portworx When you install the service, the --
storage_vendor=portworx option ensures
that the service uses the correct storage classes.
```
```
NFS When you install the service, specify the same
storage class for both file storage and block
storage.
Amazon Elastic
storage
```
```
When you install the service, you can specify:
```
```
File storage is provided by Amazon Elastic File
System. Block storage is provided by Amazon
Elastic Block Store.
```
```
NetApp Trident When you install the service, specify the same
storage class for both file storage and block
storage.
```
```
ceph-rbd
```
- **File storage:** ocs-storagecluster-cephfs
    **Block storage:** ocs-storagecluster-
    ceph-rbd

### –

```
File storage:
Either of the following storage classes:
```
### –

```
▪ ibm-spectrum-scale-sc
▪ ibm-storage-fusion-cp-sc
Block storage:
Either of the following storage classes:
```
### –

```
▪ ibm-spectrum-scale-sc
▪ ibm-storage-fusion-cp-sc
```
- **File storage:** ibm-spectrum-scale-sc
- **Block storage:** ibm-spectrum-scale-sc
- **File storage:** portworx-shared-gp3
- **Block storage:**
    ▪ portworx-cassandra-sc
    ▪ portworx-couchdb-sc
    ▪ portworx-db2-rwo-sc
    ▪ portworx-elastic-sc
    ▪ portworx-gp3-sc
    ▪ portworx-kafka-sc
    ▪ portworx-metastoredb-sc
    ▪ portworx-solr-sc
- **File storage:** managed-nfs-storage
- **Block storage:** managed-nfs-storage
- File storage only
- File storage and block storage (recommended)
- **File storage:** efs-nfs-client
**Block storage:**
Either of the following storage classes:

### –

```
▪ gp2-csi
▪ gp3-csi
```
- **File storage:** ontap-nas
- **Block storage:** ontap-nas


▾ IBM Match 360 with Watson
IBM Match 360 with Watson uses file storage and block storage.

The following storage classes are recommended for IBM Match 360 with Watson. You must specify information about the storage you

```
Storage Notes Storage classes
OpenShift Data
Foundation
```
```
When you install the service, specify file storage
and block storage.
```
```
IBM Storage Fusion
Data Foundation
```
```
When you install the service, specify file storage
and block storage.
```
```
IBM Storage Fusion
Global Data Platform
```
```
When you install the service, specify the same
storage class for both file storage and block
storage.
```
```
IBM Storage Scale
Container Native
```
```
When you install the service, specify the same
storage class for both file storage and block
storage.
Portworx When you install the service, the --
storage_vendor=portworx option ensures
that the service uses the correct storage classes.
```
```
NFS When you install the service, specify the same
storage class for both file storage and block
storage.
Amazon Elastic
storage
```
```
When you install the service, you can specify:
```
```
File storage is provided by Amazon Elastic File
System. Block storage is provided by Amazon
Elastic Block Store.
```
```
NetApp Trident When you install the service, specify the same
storage class for both file storage and block
storage.
```
- **File storage:** ocs-storagecluster-cephfs
    **Block storage:** ocs-storagecluster-
    ceph-rbd

### –

- **File storage:** ocs-storagecluster-cephfs
    **Block storage:** ocs-storagecluster-
    ceph-rbd

### –

```
File storage:
Either of the following storage classes:
```
### –

```
▪ ibm-spectrum-scale-sc
▪ ibm-storage-fusion-cp-sc
Block storage:
Either of the following storage classes:
```
### –

```
▪ ibm-spectrum-scale-sc
▪ ibm-storage-fusion-cp-sc
```
- **File storage:** ibm-spectrum-scale-sc
- **Block storage:** ibm-spectrum-scale-sc
- **File storage:** portworx-shared-gp3
- **Block storage:**
    ▪ portworx-cassandra-sc
    ▪ portworx-couchdb-sc
    ▪ portworx-db2-rwo-sc
    ▪ portworx-elastic-sc
    ▪ portworx-gp3-sc
    ▪ portworx-kafka-sc
    ▪ portworx-metastoredb-sc
    ▪ portworx-solr-sc
- **File storage:** managed-nfs-storage
- **Block storage:** managed-nfs-storage
- File storage only
- File storage and block storage (recommended)
- **File storage:** efs-nfs-client
**Block storage:**
Either of the following storage classes:

### –

```
▪ gp2-csi
▪ gp3-csi
```
- **File storage:** ontap-nas
- **Block storage:** ontap-nas


want to use when you install the service.

* indicates that the storage class is used only if common core services needs to be installed.

▾ Informix
Informix uses file storage.

The following storage classes are recommended for Informix. You must specify information about the storage you want to use when
you provision an instance of Informix.

```
Storage Notes Storage classes
OpenShift Data
Foundation
```
```
When you install the service, specify file storage
and block storage.
```
```
IBM Storage Fusion
Data Foundation
```
```
When you install the service, specify file storage
and block storage.
```
```
IBM Storage Fusion
Global Data Platform
```
```
When you install the service, specify the same
storage class for both file storage and block
storage.
```
```
IBM Storage Scale
Container Native
```
```
When you install the service, specify the same
storage class for both file storage and block
storage.
Portworx When you install the service, the --
storage_vendor=portworx option ensures
that the service uses the correct storage classes.
```
```
NFS When you install the service, specify the same
storage class for both file storage and block
storage.
Amazon Elastic
storage
```
```
When you install the service, specify file storage
and block storage.
File storage is provided by Amazon Elastic File
System. Block storage is provided by Amazon
Elastic Block Store.
```
```
NetApp Trident When you install the service, specify the same
storage class for both file storage and block
storage.
```
- **File storage:** ocs-storagecluster-cephfs
    **Block storage:** ocs-storagecluster-
    ceph-rbd

### –

- **File storage:** ocs-storagecluster-cephfs
    **Block storage:** ocs-storagecluster-
    ceph-rbd

### –

```
File storage:
Either of the following storage classes:
```
### –

```
▪ ibm-spectrum-scale-sc
▪ ibm-storage-fusion-cp-sc
Block storage:
Either of the following storage classes:
```
### –

```
▪ ibm-spectrum-scale-sc
▪ ibm-storage-fusion-cp-sc
```
- **File storage:** ibm-spectrum-scale-sc
- **Block storage:** ibm-spectrum-scale-sc
- **File storage:** portworx-shared-gp3
- **Block storage:**
    ▪ portworx-couchdb-sc*
    ▪ portworx-elastic-sc*
    ▪ portworx-gp3-sc
- **File storage:** managed-nfs-storage
- **Block storage:** managed-nfs-storage
- **File storage:** efs-nfs-client
    **Block storage:**
    Either of the following storage classes:

### –

```
▪ gp2-csi
▪ gp3-csi
```
- **File storage:** ontap-nas
- **Block storage:** ontap-nas


▾ MANTA Automated Data Lineage
MANTA Automated Data Lineage uses file storage and block storage.

The following storage classes are recommended for MANTA Automated Data Lineage. You must specify information about the storage
you want to use when you install the service.

```
Storage Notes Storage classes
OpenShift Data
Foundation
```
```
File storage: ocs-storagecluster-cephfs
```
```
IBM Storage Fusion
Data Foundation
```
```
File storage: ocs-storagecluster-cephfs
```
```
IBM Storage Fusion
Global Data Platform
```
```
File storage:
Either of the following storage classes:
```
```
IBM Storage Scale
Container Native
```
```
File storage: ibm-spectrum-scale-sc
```
```
Portworx File storage: portworx-informix-sc
```
```
NFS File storage: managed-nfs-storage
```
```
Amazon Elastic
storage
```
```
File storage is provided by Amazon Elastic File
System.
```
```
File storage: efs-nfs-client
```
```
NetApp Trident File storage: ontap-nas
```
- ibm-spectrum-scale-sc
- ibm-storage-fusion-cp-sc

```
Storage Notes Storage classes
OpenShift Data
Foundation
```
```
When you install the service, specify file storage
and block storage.
```
```
IBM Storage Fusion
Data Foundation
```
```
When you install the service, specify file storage
and block storage.
```
```
IBM Storage Fusion
Global Data Platform
```
```
When you install the service, specify the same
storage class for both file storage and block
storage.
```
```
IBM Storage Scale
Container Native
```
```
When you install the service, specify the same
storage class for both file storage and block
storage.
```
- **File storage:** ocs-storagecluster-cephfs
    **Block storage:** ocs-storagecluster-
    ceph-rbd

### –

- **File storage:** ocs-storagecluster-cephfs
    **Block storage:** ocs-storagecluster-
    ceph-rbd

### –

```
File storage:
Either of the following storage classes:
```
### –

```
▪ ibm-spectrum-scale-sc
▪ ibm-storage-fusion-cp-sc
Block storage:
Either of the following storage classes:
```
### –

```
▪ ibm-spectrum-scale-sc
▪ ibm-storage-fusion-cp-sc
```
- **File storage:** ibm-spectrum-scale-sc
- **Block storage:** ibm-spectrum-scale-sc


▾ MongoDB
MongoDB uses block storage.

The following storage classes are recommended for MongoDB. You must specify information about the storage you want to use when
you provision an instance of MongoDB.

```
Storage Notes Storage classes
Portworx When you install the service, the --
storage_vendor=portworx option ensures
that the service uses the correct storage classes.
```
```
NFS When you install the service, specify the same
storage class for both file storage and block
storage.
Amazon Elastic
storage
```
```
When you install the service, you can specify:
```
```
File storage is provided by Amazon Elastic File
System. Block storage is provided by Amazon
Elastic Block Store.
```
```
NetApp Trident When you install the service, specify the same
storage class for both file storage and block
storage.
```
- **File storage:** portworx-shared-gp3
- **Block storage:**
    ▪ portworx-cassandra-sc
    ▪ portworx-couchdb-sc
    ▪ portworx-db2-rwo-sc
    ▪ portworx-elastic-sc
    ▪ portworx-gp3-sc
    ▪ portworx-kafka-sc
    ▪ portworx-metastoredb-sc
    ▪ portworx-solr-sc
- **File storage:** managed-nfs-storage
- **Block storage:** managed-nfs-storage
- File storage only
- File storage and block storage (recommended)
- **File storage:** efs-nfs-client
**Block storage:**
Either of the following storage classes:

### –

```
▪ gp2-csi
▪ gp3-csi
```
- **File storage:** ontap-nas
- **Block storage:** ontap-nas

```
Storage Notes Storage classes
OpenShift Data
Foundation
```
```
Block storage: ocs-storagecluster-ceph-
rbd
IBM Storage Fusion
Data Foundation
```
```
Block storage: ocs-storagecluster-ceph-
rbd
IBM Storage Fusion
Global Data Platform
```
```
Block storage:
Either of the following storage classes:
```
```
IBM Storage Scale
Container Native
```
```
Block storage: ibm-spectrum-scale-sc
```
```
Portworx Block storage: portworx-db-gp
```
```
NFS Not supported. Not applicable.
```
- ibm-spectrum-scale-sc
- ibm-storage-fusion-cp-sc


▾ OpenPages
OpenPages uses file storage and block storage.

The following storage classes are recommended for OpenPages. You must specify information about the storage you want to use when
you provision the OpenPages instance.

```
Storage Notes Storage classes
Amazon Elastic
storage
```
```
Block storage is provided by Amazon Elastic
Block Store.
```
```
Block storage:
Either of the following storage classes:
```
```
NetApp Trident Not supported. Not applicable.
```
- gp2-csi
- gp3-csi

```
Restriction: This service does not support the backup and restore methods provided by the underlying storage. For example,
```
```
For information on backing up this service, see Services that support backup and restore.
```
```
If you use IBM Storage Fusion Data Foundation or IBM Storage Fusion Global Data Platform for storage, the service cannot
use IBM Spectrum Protect Plus for backups.
```
### –

- If you use Portworx for storage, the service cannot use PX-Backup for backups

```
Storage Notes Storage classes
OpenShift Data
Foundation
```
```
IBM Storage Fusion
Data Foundation
```
```
IBM Storage Fusion
Global Data Platform
```
```
Use ibm-spectrum-scale-sc for all storage.
```
- For deployments that use an internal database:
    Use ocs-storagecluster-cephfs for
    metadata storage, backup storage, and
    application file storage.

### ▪

```
Use ocs-storagecluster-ceph-rbd for
data storage.
```
### ▪

```
For deployments that use an external
database, use ocs-storagecluster-
cephfs for application file storage.
```
### –

- **File storage:** ocs-storagecluster-cephfs
    **Block storage:** ocs-storagecluster-
    ceph-rbd

### –

- For deployments that use an internal database:
    Use ocs-storagecluster-cephfs for
    metadata storage, backup storage, and
    application file storage.

### ▪

```
Use ocs-storagecluster-ceph-rbd for
data storage.
```
### ▪

```
For deployments that use an external
database, use ocs-storagecluster-
cephfs for application file storage.
```
### –

- **File storage:** ocs-storagecluster-cephfs
    **Block storage:** ocs-storagecluster-
    ceph-rbd

### –

```
File storage:
Either of the following storage classes:
```
### –

```
▪ ibm-spectrum-scale-sc
▪ ibm-storage-fusion-cp-sc
Block storage:
Either of the following storage classes:
```
### –


▾ Orchestration Pipelines

The Orchestration Pipelines leverage the storage that is provisioned when you install Watson Studio.

```
Storage Notes Storage classes
```
```
IBM Storage Scale
Container Native
```
```
Use ibm-spectrum-scale-sc for all storage.
```
```
Portworx
```
```
NFS Use managed-nfs-storage for all storage.
```
```
Amazon Elastic
storage
```
```
When you deploy the service, you can specify:
```
```
File storage is provided by Amazon Elastic File
System. Block storage is provided by Amazon
Elastic Block Store.
NetApp Trident Use ontap-nas for all storage.
```
```
▪ ibm-spectrum-scale-sc
▪ ibm-storage-fusion-cp-sc
```
- **File storage:** ibm-spectrum-scale-sc
- **Block storage:** ibm-spectrum-scale-sc
- For deployments that use an internal database:
Use portworx-rwx-gp3-sc or
portworx-shared-gp3 for application file
storage.

### ▪

```
Use portworx-db2-rwx-sc for metadata
storage and backup storage.
```
### ▪

```
Use portworx-db2-rwo-sc for data
storage
```
### ▪

```
For deployments that use an external
database, use portworx-rwx-gp3-sc or
portworx-shared-gp3 for application file
storage.
```
### –

- **File storage:**
    portworx-rwx-gp3-sc
    (Equivalent to portworx-shared-gp3 in
    older installations)

### ▪

```
▪ portworx-db2-rwx-sc
```
- **Block storage:** portworx-db2-rwo-sc
- **File storage:** managed-nfs-storage
- **Block storage:** managed-nfs-storage

```
File storage only
In this scenario, use efs-nfs-client for all
storage.
```
### –

```
File storage and block storage (recommended)
In this scenario, choose the appropriate
storage based on your environment:
```
### –

```
For deployments that use an internal
database:
```
### ▪

```
Use efs-nfs-client for metadata
storage, backup storage, and application
file storage.
```
### ▪

```
Use gp2-csi or gp3-csi for data
storage.
```
### ▪

```
For deployments that use an external
database, use efs-nfs-client for
application file storage.
```
### ▪

- **File storage:** efs-nfs-client
    **Block storage:**
    Either of the following storage classes:

### –

```
▪ gp2-csi
▪ gp3-csi
```
- **File storage:** ontap-nas
- **Block storage:** ontap-nas


▾ Planning Analytics
Planning Analytics uses file storage or a combination of file storage and block storage.

The following storage classes are recommended for Planning Analytics. You must specify information about the storage you want to use
when you provision the Planning Analytics instance.

```
Storage Notes Storage classes
OpenShift Data
Foundation
```
```
IBM Storage Fusion
Data Foundation
```
```
IBM Storage Fusion
Global Data Platform
```
```
Use ibm-spectrum-scale-sc for TM1 and
Workspace storage.
```
```
IBM Storage Scale
Container Native
```
```
Use ibm-spectrum-scale-sc for TM1 and
Workspace storage.
```
```
Portworx
```
```
NFS Use managed-nfs-storage for TM1 and
Workspace storage.
```
```
Amazon Elastic
storage
```
```
File storage is provided by Amazon Elastic File
System. Block storage is provided by Amazon
Elastic Block Store.
```
```
NetApp Trident Use ontap-nas for TM1 and Workspace storage.
```
```
Use ocs-storagecluster-cephfs for TM1
storage.
```
### –

```
Use either ocs-storagecluster-cephfs or
ocs-storagecluster-ceph-rbd for
Workspace storage.
```
### –

- **File storage:** ocs-storagecluster-cephfs
    **Block storage:** ocs-storagecluster-
    ceph-rbd

### –

```
Use ocs-storagecluster-cephfs for TM1
storage.
```
### –

```
Use either ocs-storagecluster-cephfs or
ocs-storagecluster-ceph-rbd for
Workspace storage.
```
### –

- **File storage:** ocs-storagecluster-cephfs
    **Block storage:** ocs-storagecluster-
    ceph-rbd

### –

```
File storage:
Either of the following storage classes:
```
### –

```
▪ ibm-spectrum-scale-sc
▪ ibm-storage-fusion-cp-sc
Block storage:
Either of the following storage classes:
```
### –

```
▪ ibm-spectrum-scale-sc
▪ ibm-storage-fusion-cp-sc
```
- **File storage:** ibm-spectrum-scale-sc
- **Block storage:** ibm-spectrum-scale-sc
- Use portworx-rwx-gp3-sc for TM1 storage.
Use portworx-rwx-gp3-sc, portworx-
shared-gp3, or portworx-db-gp3-sc for
Workspace storage.

### –

```
File storage: portworx-rwx-gp3-sc
(Equivalent to portworx-shared-gp3 in
older installations)
```
### –

- **Block storage:** portworx-db-gp3-sc
- **File storage:** managed-nfs-storage
- **Block storage:** managed-nfs-storage
- Use efs-nfs-client for TM1 storage.
Use efs-nfs-client, gp2-csi, or gp3-csi
for Workspace storage.

### –

- **File storage:** efs-nfs-client
    **Block storage:**
    Either of the following storage classes:

### –

```
▪ gp2-csi
▪ gp3-csi
```
- **File storage:** ontap-nas
- **Block storage:** ontap-nas


▾ Product Master
Product Master uses file storage and block storage.

The following storage classes are recommended for Product Master. You must specify information about the storage you want to use
when you provision the Product Master instance.

▾ RStudio Server Runtimes
RStudio Server Runtimes leverages the storage that is provisioned when you install Watson Studio.

▾ SPSS Modeler

```
Storage Notes Storage classes
OpenShift Data
Foundation
```
```
When you create the service instance, specify file
storage and block storage.
```
```
IBM Storage Fusion
Data Foundation
```
```
When you create the service instance, specify file
storage and block storage.
```
```
IBM Storage Fusion
Global Data Platform
```
```
When you create the service instance, specify the
same storage class for both file storage and block
storage.
```
```
IBM Storage Scale
Container Native
```
```
When you create the service instance, specify the
same storage class for both file storage and block
storage.
Portworx When you create the service instance, specify file
storage and block storage.
```
```
NFS Not supported. Not applicable.
```
```
Amazon Elastic
storage
```
```
When you create the service instance, specify file
storage and block storage.
File storage is provided by Amazon Elastic File
System. Block storage is provided by Amazon
Elastic Block Store.
```
```
NetApp Trident When you create the service instance, specify the
same storage class for both file storage and block
storage.
```
- **File storage:** ocs-storagecluster-cephfs
    **Block storage:** ocs-storagecluster-
    ceph-rbd

### –

- **File storage:** ocs-storagecluster-cephfs
    **Block storage:** ocs-storagecluster-
    ceph-rbd

### –

```
File storage:
Either of the following storage classes:
```
### –

```
▪ ibm-spectrum-scale-sc
▪ ibm-storage-fusion-cp-sc
Block storage:
Either of the following storage classes:
```
### –

```
▪ ibm-spectrum-scale-sc
▪ ibm-storage-fusion-cp-sc
```
- **File storage:** ibm-spectrum-scale-sc
- **Block storage:** ibm-spectrum-scale-sc

```
File storage: portworx-rwx-gp3-sc
(Equivalent to portworx-shared-gp3 in
older installations)
```
### –

- **Block storage:** portworx-gp3-sc
- **File storage:** efs-nfs-client
    **Block storage:**
    Either of the following storage classes:

### –

```
▪ gp2-csi
▪ gp3-csi
```
- **File storage:** ontap-nas
- **Block storage:** ontap-nas


SPSS Modeler leverages the storage that is provisioned when you install Watson Studio.

▾ Synthetic Data Generator
Synthetic Data Generator uses the file storage and block storage that is provisioned for common core services.

The following storage classes are recommended for common core services. You must specify information about the storage you want to
use when you install the service.

```
Storage Notes Storage classes
OpenShift Data
Foundation
```
```
When you install the service, specify file storage
and block storage.
```
```
IBM Storage Fusion
Data Foundation
```
```
When you install the service, specify file storage
and block storage.
```
```
IBM Storage Fusion
Global Data Platform
```
```
When you install the service, specify the same
storage class for both file storage and block
storage.
```
```
IBM Storage Scale
Container Native
```
```
When you install the service, specify the same
storage class for both file storage and block
storage.
Portworx When you install the service, the --
storage_vendor=portworx option ensures
that the service uses the correct storage classes.
```
```
NFS When you install the service, specify the same
storage class for both file storage and block
storage.
Amazon Elastic
storage
```
```
When you install the service, you can specify:
```
```
File storage is provided by Amazon Elastic File
System. Block storage is provided by Amazon
Elastic Block Store.
```
```
NetApp Trident When you install the service, specify the same
storage class for both file storage and block
storage.
```
- **File storage:** ocs-storagecluster-cephfs
    **Block storage:** ocs-storagecluster-
    ceph-rbd

### –

- **File storage:** ocs-storagecluster-cephfs
    **Block storage:** ocs-storagecluster-
    ceph-rbd

### –

```
File storage:
Either of the following storage classes:
```
### –

```
▪ ibm-spectrum-scale-sc
▪ ibm-storage-fusion-cp-sc
Block storage:
Either of the following storage classes:
```
### –

```
▪ ibm-spectrum-scale-sc
▪ ibm-storage-fusion-cp-sc
```
- **File storage:** ibm-spectrum-scale-sc
- **Block storage:** ibm-spectrum-scale-sc

```
File storage: portworx-rwx-gp3-sc
(Equivalent to portworx-shared-gp3 in
older installations)
```
### –

- **Block storage:**
    ▪ portworx-couchdb-sc
    ▪ portworx-elastic-sc
    ▪ portworx-gp3-sc
- **File storage:** managed-nfs-storage
- **Block storage:** managed-nfs-storage
- File storage only
- File storage and block storage (recommended)
- **File storage:** efs-nfs-client
**Block storage:**
Either of the following storage classes:

### –

```
▪ gp2-csi
▪ gp3-csi
```
- **File storage:** ontap-nas
- **Block storage:** ontap-nas


▾ Voice Gateway
You can optionally install Voice Gateway without specifying any storage. However, if you want to retain logs or voice recordings, you can
update the custom resource for the service to specify file storage.

The following storage classes are recommended for Voice Gateway.

▾ Watson Discovery
Watson Discovery uses file storage and block storage.

The following storage classes are recommended for Watson Discovery. You must specify information about the storage you want to use
when you install the service.

```
Storage Notes Storage classes
OpenShift Data
Foundation
```
```
You can use ocs-storagecluster-cephfs to
store logs or voice recordings.
```
```
File storage: ocs-storagecluster-cephfs
```
```
IBM Storage Fusion
Data Foundation
```
```
You can use ocs-storagecluster-cephfs to
store logs or voice recordings.
```
```
File storage: ocs-storagecluster-cephfs
```
```
IBM Storage Fusion
Global Data Platform
```
```
You can use ibm-spectrum-scale-sc to store
logs or voice recordings.
```
```
File storage:
Either of the following storage classes:
```
```
IBM Storage Scale
Container Native
```
```
You can use ibm-spectrum-scale-sc to store
logs or voice recordings.
```
```
File storage: ibm-spectrum-scale-sc
```
```
Portworx You can use portworx-rwx-gp3-sc or
portworx-shared-gp3 to store logs or voice
recordings.
```
```
File storage: portworx-rwx-gp3-sc
(Equivalent to portworx-shared-gp3 in older
installations)
```
```
NFS Not supported. Not applicable.
```
```
Amazon Elastic
storage
```
```
Not supported. Not applicable.
```
```
NetApp Trident Not supported. Not applicable.
```
- ibm-spectrum-scale-sc
- ibm-storage-fusion-cp-sc

```
Restriction: This service does not support the backup and restore methods provided by the underlying storage. For example,
```
```
For information on backing up this service, see Services that support backup and restore.
```
```
If you use IBM Storage Fusion Data Foundation or IBM Storage Fusion Global Data Platform for storage, the service cannot
use IBM Spectrum Protect Plus for backups.
```
### –

- If you use Portworx for storage, the service cannot use PX-Backup for backups

```
Storage Notes Storage classes
OpenShift Data
Foundation
```
```
When you install the service, specify file storage
and block storage.
```
```
IBM Storage Fusion
Data Foundation
```
```
When you install the service, specify file storage
and block storage.
```
- **File storage:** ocs-storagecluster-cephfs
    **Block storage:** ocs-storagecluster-
    ceph-rbd

### –

- **File storage:** ocs-storagecluster-cephfs
- **Block storage:** ocs-storagecluster-


▾ Watson Machine Learning
Watson Machine Learning uses file storage and block storage.

The following storage classes are recommended for Watson Machine Learning. You must specify information about the storage you
want to use when you install the service.

* indicates that the storage class is used only if common core services needs to be installed.

```
Storage Notes Storage classes
```
```
IBM Storage Fusion
Global Data Platform
```
```
When you install the service, specify the same
storage class for both file storage and block
storage.
```
```
IBM Storage Scale
Container Native
```
```
When you install the service, specify the same
storage class for both file storage and block
storage.
Portworx When you install the service, the --
storage_vendor=portworx option ensures
that the service uses the correct storage classes.
NFS Not supported. Not applicable.
```
```
Amazon Elastic
storage
```
```
When you install the service, specify file storage
and block storage.
File storage is provided by Amazon Elastic File
System. Block storage is provided by Amazon
Elastic Block Store.
```
```
NetApp Trident When you install the service, specify the same
storage class for both file storage and block
storage.
```
```
ceph-rbd
```
```
File storage:
Either of the following storage classes:
```
### –

```
▪ ibm-spectrum-scale-sc
▪ ibm-storage-fusion-cp-sc
Block storage:
Either of the following storage classes:
```
### –

```
▪ ibm-spectrum-scale-sc
▪ ibm-storage-fusion-cp-sc
```
- **File storage:** ibm-spectrum-scale-sc
- **Block storage:** ibm-spectrum-scale-sc
- **File storage:** portworx-rwx-gp3-sc
- **Block storage:** portworx-db-gp2-sc
- **File storage:** efs-nfs-client
    **Block storage:**
    Either of the following storage classes:

### –

```
▪ gp2-csi
▪ gp3-csi
```
- **File storage:** ontap-nas
- **Block storage:** ontap-nas

```
Storage Notes Storage classes
OpenShift Data
Foundation
```
```
When you install the service, specify file storage
and block storage.
```
```
IBM Storage Fusion
Data Foundation
```
```
When you install the service, specify file storage
and block storage.
```
```
IBM Storage Fusion
Global Data Platform
```
```
When you install the service, specify the same
storage class for both file storage and block
```
- **File storage:** ocs-storagecluster-cephfs
    **Block storage:** ocs-storagecluster-
    ceph-rbd

### –

- **File storage:** ocs-storagecluster-cephfs
    **Block storage:** ocs-storagecluster-
    ceph-rbd

### –

```
File storage:
Either of the following storage classes:
```
### –


▾ Watson Machine Learning Accelerator
Watson Machine Learning Accelerator uses file storage.

The following storage classes are recommended for Watson Machine Learning Accelerator. You must specify information about the
storage you want to use when you install the service.

```
Storage Notes Storage classes
storage.
```
```
IBM Storage Scale
Container Native
```
```
When you install the service, specify the same
storage class for both file storage and block
storage.
Portworx When you install the service, the --
storage_vendor=portworx option ensures
that the service uses the correct storage classes.
```
```
NFS When you install the service, specify the same
storage class for both file storage and block
storage.
Amazon Elastic
storage
```
```
When you install the service, you can specify:
```
```
File storage is provided by Amazon Elastic File
System. Block storage is provided by Amazon
Elastic Block Store.
```
```
NetApp Trident When you install the service, specify the same
storage class for both file storage and block
storage.
```
```
▪ ibm-spectrum-scale-sc
▪ ibm-storage-fusion-cp-sc
Block storage:
Either of the following storage classes:
```
### –

```
▪ ibm-spectrum-scale-sc
▪ ibm-storage-fusion-cp-sc
```
- **File storage:** ibm-spectrum-scale-sc
- **Block storage:** ibm-spectrum-scale-sc

```
File storage: portworx-rwx-gp3-sc
(Equivalent to portworx-shared-gp3 in
older installations)
```
### –

- **Block storage:**
    ▪ portworx-gp3-sc
    ▪ portworx-couchdb-sc*
    ▪ portworx-elastic-sc*
- **File storage:** managed-nfs-storage
- **Block storage:** managed-nfs-storage
- File storage only
- File storage and block storage (recommended)
- **File storage:** efs-nfs-client
**Block storage:**
Either of the following storage classes:

### –

```
▪ gp2-csi
▪ gp3-csi
```
- **File storage:** ontap-nas
- **Block storage:** ontap-nas

```
Storage Notes Storage classes
OpenShift Data
Foundation
```
```
When you install the service, specify file storage.
If you specify block storage, the service ignores
this information.
```
```
File storage: ocs-storagecluster-cephfs
```
```
IBM Storage Fusion
Data Foundation
```
```
When you install the service, specify file storage.
If you specify block storage, the service ignores
this information.
```
```
File storage: ocs-storagecluster-cephfs
```
```
IBM Storage Fusion
Global Data Platform
```
```
When you install the service, specify file storage.
If you specify block storage, the service ignores
this information.
```
```
File storage:
Either of the following storage classes:
```

▾ Watson OpenScale
Watson OpenScale uses file storage and block storage.

The following storage classes are recommended for Watson OpenScale. You must specify information about the storage you want to
use when you install the service.

```
Storage Notes Storage classes
```
```
IBM Storage Scale
Container Native
```
```
When you install the service, specify file storage.
If you specify block storage, the service ignores
this information.
```
```
File storage: ibm-spectrum-scale-sc
```
```
Portworx When you install the service, the --
storage_vendor=portworx option ensures
that the service uses the correct storage classes.
```
```
File storage: portworx-rwx-gp3-sc
(Equivalent to portworx-shared-gp3 in older
installations)
```
```
NFS When you install the service, specify file storage.
If you specify block storage, the service ignores
this information.
```
```
File storage: managed-nfs-storage
```
```
Amazon Elastic
storage
```
```
When you install the service, specify file storage.
If you specify block storage, the service ignores
this information.
File storage is provided by Amazon Elastic File
System.
```
```
File storage: efs-nfs-client
```
```
NetApp Trident When you install the service, specify file storage.
If you specify block storage, the service ignores
this information.
```
```
File storage: ontap-nas
```
- ibm-spectrum-scale-sc
- ibm-storage-fusion-cp-sc

```
Storage Notes Storage classes
OpenShift Data
Foundation
```
```
When you install the service, specify file storage
and block storage.
```
```
IBM Storage Fusion
Data Foundation
```
```
When you install the service, specify file storage
and block storage.
```
```
IBM Storage Fusion
Global Data Platform
```
```
When you install the service, specify the same
storage class for both file storage and block
storage.
```
- **File storage:** ocs-storagecluster-cephfs
    **Block storage:** ocs-storagecluster-
    ceph-rbd

### –

- **File storage:** ocs-storagecluster-cephfs
    **Block storage:** ocs-storagecluster-
    ceph-rbd

### –

```
File storage:
Either of the following storage classes:
```
### –

```
▪ ibm-spectrum-scale-sc
▪ ibm-storage-fusion-cp-sc
Block storage:
Either of the following storage classes:
```
### –

```
▪ ibm-spectrum-scale-sc
▪ ibm-storage-fusion-cp-sc
```

▾ Watson Speech services
Watson Speech services use file storage and block storage.

The following storage classes are recommended for Watson Speech services. You must specify information about the storage you want
to use when you install the service.

```
Storage Notes Storage classes
IBM Storage Scale
Container Native
```
```
When you install the service, specify the same
storage class for both file storage and block
storage.
Portworx When you install the service, the --
storage_vendor=portworx option ensures
that the service uses the correct storage classes.
NFS When you install the service, specify the same
storage class for both file storage and block
storage.
Amazon Elastic
storage
```
```
When you install the service, you can specify:
```
```
File storage is provided by Amazon Elastic File
System. Block storage is provided by Amazon
Elastic Block Store.
```
```
NetApp Trident When you install the service, specify the same
storage class for both file storage and block
storage.
```
- **File storage:** ibm-spectrum-scale-sc
- **Block storage:** ibm-spectrum-scale-sc
- **File storage:** portworx-shared-gp3
- **Block storage:** portworx-gp3-sc
- **File storage:** managed-nfs-storage
- **Block storage:** managed-nfs-storage
- File storage only
- File storage and block storage (recommended)
- **File storage:** efs-nfs-client
**Block storage:**
Either of the following storage classes:

### –

```
▪ gp2-csi
▪ gp3-csi
```
- **File storage:** ontap-nas
- **Block storage:** ontap-nas

```
Storage Notes Storage classes
OpenShift Data
Foundation
```
```
When you install the service, specify file storage
and block storage.
```
```
IBM Storage Fusion
Data Foundation
```
```
When you install the service, specify file storage
and block storage.
```
```
IBM Storage Fusion
Global Data Platform
```
```
When you install the service, specify the same
storage class for both file storage and block
storage.
```
```
IBM Storage Scale
Container Native
```
```
When you install the service, specify the same
storage class for both file storage and block
storage.
```
- **File storage:** ocs-storagecluster-cephfs
    **Block storage:** ocs-storagecluster-
    ceph-rbd

### –

- **File storage:** ocs-storagecluster-cephfs
    **Block storage:** ocs-storagecluster-
    ceph-rbd

### –

```
File storage:
Either of the following storage classes:
```
### –

```
▪ ibm-spectrum-scale-sc
▪ ibm-storage-fusion-cp-sc
Block storage:
Either of the following storage classes:
```
### –

```
▪ ibm-spectrum-scale-sc
▪ ibm-storage-fusion-cp-sc
```
- **File storage:** ibm-spectrum-scale-sc
- **Block storage:** ibm-spectrum-scale-sc


▾ Watson Studio
Watson Studio uses file storage and block storage.

The following storage classes are recommended for Watson Studio. You must specify information about the storage you want to use
when you install the service.

```
Storage Notes Storage classes
Portworx When you install the service, the --
storage_vendor=portworx option ensures
that the service uses the correct storage classes.
NFS Not supported. Not applicable.
```
```
Amazon Elastic
storage
```
```
When you install the service, specify file storage
and block storage.
File storage is provided by Amazon Elastic File
System. Block storage is provided by Amazon
Elastic Block Store.
```
```
NetApp Trident When you install the service, specify the same
storage class for both file storage and block
storage.
```
- **File storage:** portworx-shared-gp3
- **Block storage:** portworx-db-gp3-sc
- **File storage:** efs-nfs-client
    **Block storage:**
    Either of the following storage classes:

### –

```
▪ gp2-csi
▪ gp3-csi
```
- **File storage:** ontap-nas
- **Block storage:** ontap-nas

```
Storage Notes Storage classes
OpenShift Data
Foundation
```
```
When you install the service, specify file storage
and block storage.
```
```
IBM Storage Fusion
Data Foundation
```
```
When you install the service, specify file storage
and block storage.
```
```
IBM Storage Fusion
Global Data Platform
```
```
When you install the service, specify the same
storage class for both file storage and block
storage.
```
```
IBM Storage Scale
Container Native
```
```
When you install the service, specify the same
storage class for both file storage and block
storage.
Portworx When you install the service, the --
storage_vendor=portworx option ensures
that the service uses the correct storage classes.
```
- **File storage:** ocs-storagecluster-cephfs
    **Block storage:** ocs-storagecluster-
    ceph-rbd

### –

- **File storage:** ocs-storagecluster-cephfs
    **Block storage:** ocs-storagecluster-
    ceph-rbd

### –

```
File storage:
Either of the following storage classes:
```
### –

```
▪ ibm-spectrum-scale-sc
▪ ibm-storage-fusion-cp-sc
Block storage:
Either of the following storage classes:
```
### –

```
▪ ibm-spectrum-scale-sc
▪ ibm-storage-fusion-cp-sc
```
- **File storage:** ibm-spectrum-scale-sc
- **Block storage:** ibm-spectrum-scale-sc

```
File storage: portworx-rwx-gp3-sc
(Equivalent to portworx-shared-gp3 in
older installations)
```
### –

- **Block storage:**
    ▪ portworx-couchdb-sc


▾ Watson Studio Runtimes

The Watson Studio Runtimes leverage the storage that is provisioned when you install Watson Studio.

▾ watsonx.ai
IBM watsonx.ai uses file storage and block storage.

The following storage classes are recommended for watsonx.ai. You must specify information about the storage you want to use when
you install the service.

```
Storage Notes Storage classes
```
```
NFS When you install the service, specify the same
storage class for both file storage and block
storage.
Amazon Elastic
storage
```
```
When you install the service, you can specify:
```
```
File storage is provided by Amazon Elastic File
System. Block storage is provided by Amazon
Elastic Block Store.
```
```
NetApp Trident When you install the service, specify the same
storage class for both file storage and block
storage.
```
```
▪ portworx-elastic-sc
▪ portworx-gp3-sc
```
- **File storage:** managed-nfs-storage
- **Block storage:** managed-nfs-storage
- File storage only
- File storage and block storage (recommended)
- **File storage:** efs-nfs-client
**Block storage:**
Either of the following storage classes:

### –

```
▪ gp2-csi
▪ gp3-csi
```
- **File storage:** ontap-nas
- **Block storage:** ontap-nas

```
Storage Notes Storage classes
OpenShift Data
Foundation
```
```
When you install the service, specify file storage
and block storage.
```
```
IBM Storage Fusion
Data Foundation
```
```
When you install the service, specify file storage
and block storage.
```
```
IBM Storage Fusion
Global Data Platform
```
```
When you install the service, specify the same
storage class for both file storage and block
storage.
```
```
IBM Storage Scale
Container Native
```
```
When you install the service, specify the same
storage class for both file storage and block
storage.
```
- **File storage:** ocs-storagecluster-cephfs
    **Block storage:** ocs-storagecluster-
    ceph-rbd

### –

- **File storage:** ocs-storagecluster-cephfs
    **Block storage:** ocs-storagecluster-
    ceph-rbd

### –

```
File storage:
Either of the following storage classes:
```
### –

```
▪ ibm-spectrum-scale-sc
▪ ibm-storage-fusion-cp-sc
Block storage:
Either of the following storage classes:
```
### –

```
▪ ibm-spectrum-scale-sc
▪ ibm-storage-fusion-cp-sc
```
- **File storage:** ibm-spectrum-scale-sc
- **Block storage:** ibm-spectrum-scale-sc


▾ watsonx Assistant
watsonx Assistant uses file storage and block storage.

The following storage classes are recommended for watsonx Assistant. You must specify information about the storage you want to use
when you install the service.

```
Storage Notes Storage classes
Portworx When you install the service, the --
storage_vendor=portworx option ensures
that the service uses the correct storage classes.
```
```
NFS When you install the service, specify the same
storage class for both file storage and block
storage.
Amazon Elastic
storage
```
```
When you install the service, specify file storage.
If you specify block storage, the service ignores
this information.
File storage is provided by Amazon Elastic File
System.
```
```
File storage: efs-nfs-client
```
```
File storage: portworx-rwx-gp3-sc
(Equivalent to portworx-shared-gp3 in
older installations)
```
### –

- **Block storage:**
    ▪ portworx-couchdb-sc
    ▪ portworx-elastic-sc
    ▪ portworx-gp3-sc
- **File storage:** managed-nfs-storage
- **Block storage:** managed-nfs-storage

```
Storage Notes Storage classes
OpenShift Data
Foundation
```
```
When you install the service, specify file storage
and block storage.
```
```
IBM Storage Fusion
Data Foundation
```
```
When you install the service, specify file storage
and block storage.
```
```
IBM Storage Fusion
Global Data Platform
```
```
When you install the service, specify the same
storage class for both file storage and block
storage.
```
```
IBM Storage Scale
Container Native
```
```
When you install the service, specify the same
storage class for both file storage and block
storage.
```
- **File storage:** ocs-storagecluster-cephfs
    **Block storage:** ocs-storagecluster-
    ceph-rbd

### –

- **File storage:** ocs-storagecluster-cephfs
    **Block storage:** ocs-storagecluster-
    ceph-rbd

### –

```
File storage:
Either of the following storage classes:
```
### –

```
▪ ibm-spectrum-scale-sc
▪ ibm-storage-fusion-cp-sc
Block storage:
Either of the following storage classes:
```
### –

```
▪ ibm-spectrum-scale-sc
▪ ibm-storage-fusion-cp-sc
```
- **File storage:** ibm-spectrum-scale-sc
- **Block storage:** ibm-spectrum-scale-sc


▾ watsonx Code Assistant for Red Hat Ansible Lightspeed
watsonx Code Assistant for Red Hat Ansible Lightspeed uses file storage and block storage.

The following storage classes are recommended for watsonx Code Assistant for Red Hat Ansible Lightspeed. You must specify
information about the storage you want to use when you install the service.

```
Storage Notes Storage classes
Portworx When you install the service, the --
storage_vendor=portworx option ensures
that the service uses the correct storage classes.
```
```
NFS Not supported. Not applicable.
```
```
Amazon Elastic
storage
```
```
When you install the service, specify file storage
and block storage.
File storage is provided by Amazon Elastic File
System. Block storage is provided by Amazon
Elastic Block Store.
```
```
NetApp Trident When you install the service, specify the same
storage class for both file storage and block
storage.
```
- **File storage:** portworx-shared-gp3
    **Block storage:** portworx-watson-
    assistant-sc

### –

- **File storage:** efs-nfs-client
    **Block storage:**
    Either of the following storage classes:

### –

```
▪ gp2-csi
▪ gp3-csi
```
- **File storage:** ontap-nas
- **Block storage:** ontap-nas

```
Storage Notes Storage classes
OpenShift Data
Foundation
```
```
When you install the service, specify file storage
and block storage.
```
```
IBM Storage Fusion
Data Foundation
```
```
When you install the service, specify file storage
and block storage.
```
```
IBM Storage Fusion
Global Data Platform
```
```
When you install the service, specify the same
storage class for both file storage and block
storage.
```
```
IBM Storage Scale
Container Native
```
```
When you install the service, specify the same
storage class for both file storage and block
storage.
Portworx When you install the service, the --
storage_vendor=portworx option ensures
that the service uses the correct storage classes.
```
- **File storage:** ocs-storagecluster-cephfs
    **Block storage:** ocs-storagecluster-
    ceph-rbd

### –

- **File storage:** ocs-storagecluster-cephfs
    **Block storage:** ocs-storagecluster-
    ceph-rbd

### –

```
File storage:
Either of the following storage classes:
```
### –

```
▪ ibm-spectrum-scale-sc
▪ ibm-storage-fusion-cp-sc
Block storage:
Either of the following storage classes:
```
### –

```
▪ ibm-spectrum-scale-sc
▪ ibm-storage-fusion-cp-sc
```
- **File storage:** ibm-spectrum-scale-sc
- **Block storage:** ibm-spectrum-scale-sc
- **File storage:** portworx-shared-gp3
    **Block storage:** portworx-watson-
    assistant-sc

### –


▾ watsonx Code Assistant for Z
watsonx Code Assistant for Z uses file storage and block storage.

The following storage classes are recommended for watsonx Code Assistant for Z. You must specify information about the storage you
want to use when you install the service.

```
Storage Notes Storage classes
NFS When you install the service, specify the same
storage class for both file storage and block
storage.
Amazon Elastic
storage
```
```
When you install the service, specify file storage
and block storage.
File storage is provided by Amazon Elastic File
System. Block storage is provided by Amazon
Elastic Block Store.
```
```
NetApp Trident When you install the service, specify the same
storage class for both file storage and block
storage.
```
- **File storage:** managed-nfs-storage
- **Block storage:** managed-nfs-storage
- **File storage:** efs-nfs-client
    **Block storage:**
    Either of the following storage classes:

### –

```
▪ gp2-csi
▪ gp3-csi
```
- **File storage:** ontap-nas
- **Block storage:** ontap-nas

```
Storage Notes Storage classes
OpenShift Data
Foundation
```
```
When you install the service, specify file storage
and block storage.
```
```
IBM Storage Fusion
Data Foundation
```
```
When you install the service, specify file storage
and block storage.
```
```
IBM Storage Fusion
Global Data Platform
```
```
When you install the service, specify the same
storage class for both file storage and block
storage.
```
```
IBM Storage Scale
Container Native
```
```
When you install the service, specify the same
storage class for both file storage and block
storage.
Portworx When you install the service, the --
storage_vendor=portworx option ensures
that the service uses the correct storage classes.
```
```
NFS When you install the service, specify the same
storage class for both file storage and block
storage.
```
- **File storage:** ocs-storagecluster-cephfs
    **Block storage:** ocs-storagecluster-
    ceph-rbd

### –

- **File storage:** ocs-storagecluster-cephfs
    **Block storage:** ocs-storagecluster-
    ceph-rbd

### –

```
File storage:
Either of the following storage classes:
```
### –

```
▪ ibm-spectrum-scale-sc
▪ ibm-storage-fusion-cp-sc
Block storage:
Either of the following storage classes:
```
### –

```
▪ ibm-spectrum-scale-sc
▪ ibm-storage-fusion-cp-sc
```
- **File storage:** ibm-spectrum-scale-sc
- **Block storage:** ibm-spectrum-scale-sc
- **File storage:** portworx-shared-gp3
    **Block storage:** portworx-watson-
    assistant-sc

### –

- **File storage:** managed-nfs-storage
- **Block storage:** managed-nfs-storage


▾ watsonx.data
watsonx.data uses block storage.

The following storage classes are recommended for watsonx.data. You must specify information about the storage you want to use
when you install the service.

▾ watsonx.governance

```
Storage Notes Storage classes
Amazon Elastic
storage
```
```
When you install the service, specify file storage
and block storage.
File storage is provided by Amazon Elastic File
System. Block storage is provided by Amazon
Elastic Block Store.
```
```
NetApp Trident When you install the service, specify the same
storage class for both file storage and block
storage.
```
- **File storage:** efs-nfs-client
    **Block storage:**
    Either of the following storage classes:

### –

```
▪ gp2-csi
▪ gp3-csi
```
- **File storage:** ontap-nas
- **Block storage:** ontap-nas

```
Storage Notes Storage classes
OpenShift Data
Foundation
```
```
When you install the service, specify block
storage.If you specify file storage, the service
ignores this information.
```
```
Block storage: ocs-storagecluster-ceph-
rbd
```
```
IBM Storage Fusion
Data Foundation
```
```
When you install the service, specify block
storage.If you specify file storage, the service
ignores this information.
```
```
Block storage: ocs-storagecluster-ceph-
rbd
```
```
IBM Storage Fusion
Global Data Platform
```
```
When you install the service, specify block
storage.If you specify file storage, the service
ignores this information.
```
```
Block storage:
Either of the following storage classes:
```
```
IBM Storage Scale
Container Native
```
```
When you install the service, specify block
storage.If you specify file storage, the service
ignores this information.
```
```
Block storage: ibm-spectrum-scale-sc
```
```
Portworx When you install the service, the --
storage_vendor=portworx option ensures
that the service uses the correct storage classes.
```
```
Block storage: portworx-db-gp
```
```
NFS When you install the service, specify block
storage.If you specify file storage, the service
ignores this information.
```
```
Block storage: managed-nfs-storage
```
```
Amazon Elastic
storage
```
```
When you install the service, specify block
storage.If you specify file storage, the service
ignores this information.
Block storage is provided by Amazon Elastic
Block Store.
```
```
Block storage:
Either of the following storage classes:
```
```
NetApp Trident When you install the service, specify block
storage.If you specify file storage, the service
ignores this information.
```
```
Block storage: ontap-nas
```
- ibm-spectrum-scale-sc
- ibm-storage-fusion-cp-sc
- gp2-csi
- gp3-csi


watsonx.governance uses file storage and block storage.

The following storage classes are recommended for watsonx.governance. You must specify information about the storage you want to
use when you install the service.

▾ watsonx Orchestrate
watsonx Orchestrate uses file storage and block storage.

The following storage classes are recommended for watsonx Orchestrate. You must specify information about the storage you want to
use when you install the service.

```
Storage Notes Storage classes
OpenShift Data
Foundation
```
```
When you install the service, specify file storage
and block storage.
```
```
IBM Storage Fusion
Data Foundation
```
```
When you install the service, specify file storage
and block storage.
```
```
IBM Storage Fusion
Global Data Platform
```
```
When you install the service, specify the same
storage class for both file storage and block
storage.
```
```
IBM Storage Scale
Container Native
```
```
When you install the service, specify the same
storage class for both file storage and block
storage.
Portworx When you install the service, the --
storage_vendor=portworx option ensures
that the service uses the correct storage classes.
NFS When you install the service, specify the same
storage class for both file storage and block
storage.
Amazon Elastic
storage
```
```
When you install the service, specify file storage
and block storage.
File storage is provided by Amazon Elastic File
System.Block storage is provided by Amazon
Elastic Block Store.
```
```
NetApp Trident When you install the service, specify the same
storage class for both file storage and block
storage.
```
- **File storage:** ocs-storagecluster-cephfs
    **Block storage:** ocs-storagecluster-
    ceph-rbd

### –

- **File storage:** ocs-storagecluster-cephfs
    **Block storage:** ocs-storagecluster-
    ceph-rbd

### –

```
File storage:
Either of the following storage classes:
```
### –

```
▪ ibm-spectrum-scale-sc
▪ ibm-storage-fusion-cp-sc
Block storage:
Either of the following storage classes:
```
### –

```
▪ ibm-spectrum-scale-sc
▪ ibm-storage-fusion-cp-sc
```
- **File storage:** ibm-spectrum-scale-sc
- **Block storage:** ibm-spectrum-scale-sc
- **File storage:** portworx-shared-gp3
- **Block storage:** portworx-gp3-sc
- **File storage:** managed-nfs-storage
- **Block storage:** managed-nfs-storage
- **File storage:** efs-nfs-client
    **Block storage:**
    Either of the following storage classes:

### –

```
▪ gp2-csi
▪ gp3-csi
```
- **File storage:** ontap-nas
- **Block storage:** ontap-nas

```
Storage Notes Storage classes
```

**Parent topic:**

```
System requirements
```
**Storage Notes Storage classes**
OpenShift Data
Foundation

```
When you install the service, specify file storage
and block storage.
```
IBM Storage Fusion
Data Foundation

```
When you install the service, specify file storage
and block storage.
```
IBM Storage Fusion
Global Data Platform

```
Not supported. Not applicable.
```
IBM Storage Scale
Container Native

```
Not supported. Not applicable.
```
Portworx When you install the service, the --
storage_vendor=portworx option ensures
that the service uses the correct storage classes.
NFS Not supported. Not applicable.

Amazon Elastic
storage

```
Not supported. Not applicable.
```
NetApp Trident Not supported. Not applicable.

- **File storage:** ocs-storagecluster-cephfs
    **Block storage:** ocs-storagecluster-
    ceph-rbd

### –

- **File storage:** ocs-storagecluster-cephfs
    **Block storage:** ocs-storagecluster-
    ceph-rbd

### –

- **File storage:** portworx-shared-gp3
- **Block storage:** portworx-db-gp3-sc


