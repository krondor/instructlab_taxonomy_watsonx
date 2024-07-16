# Storage architecture for IBM Cloud Pak

# for Data

Last Updated: 2024-06-

IBM Cloud Pak for Data supports numerous types of persistent storage. The way that you choose to
deploy storage in relation to your cluster depends on which type of persistent storage you're using.

Cloud Pak for Data supports the following types of persistent storage:

If possible, choose a storage provider that is supported by all of the services that you plan to install. If
that is not possible, your cluster can contain a mix of storage types. However, each service can target
only one type of storage.

For specific storage considerations and requirements, see the following information:

▾ Red Hat OpenShift Data Foundation storage
If you are using OpenShift Data Foundation, you can use either of the following configurations:

- Red Hat® OpenShift® Data Foundation storage
- IBM Storage Fusion Data Foundation storage
- IBM Storage Fusion Global Data Platform storage
- IBM Storage Scale Container Native storage
- Portworx storage
- NFS storage
- AWS with EFS storage only
- AWS with EFS and EBS storage
- NetApp Trident storage

```
Storage considerations
You must have a supported persistent storage solution that is accessible to your Red Hat OpenShift
cluster and meets the stated requirements. For example, if your network speeds are too slow or if the
disks do not have sufficient I/O performance, services can experience poor performance or cluster
instability.
```
## –

```
Storage requirements
Ensure that you install the software on persistent storage that works with the services that you plan
to install.
```
## –

- You can use dedicated storage nodes.
- Your storage nodes can co-exist with your worker nodes.


Because OpenShift Data Foundation uses 3 replicas, it is recommended that you deploy OpenShift Data
Foundation on nodes in multiples of three. This makes it easier to set up the initial storage cluster and
scale up your storage capacity.

▾ IBM Storage Fusion Data Foundation storage
If you are using IBM Storage Fusion Data Foundation, you can use either of the following
configurations:

Because OpenShift Data Foundation uses 3 replicas, it is recommended that you deploy OpenShift Data
Foundation on nodes in multiples of three. This makes it easier to set up the initial storage cluster and
scale up your storage capacity.

▾ IBM Storage Fusion Global Data Platform storage

**IBM Storage Fusion**

```
IBM Storage Fusion Global Data Platform connects to your IBM Storage Scale cluster through a
remote network mount to provide access to the high-performance General Parallel File System
(GPFS). IBM Storage Fusion Global Data Platform provides persistent data storage through the IBM
Storage Scale Container Storage Interface Driver.
```
```
Both IBM Storage Fusion Global Data Platform and IBM Storage Scale Container Storage Interface
Driver are deployed on the worker nodes of your OpenShift cluster.
```
**IBM Storage Fusion HCI System**

```
If you're using IBM Storage Fusion HCI System, IBM Storage Fusion Global Data Platform connects
to your IBM Storage Scale Storage Cluster through Erasure Code Edition (ECE) disks to provide
access to the General Parallel File System (GPFS). IBM Storage Fusion Global Data Platform
provides persistent data storage through the IBM Storage Scale Container Storage Interface Driver.
```
```
Both IBM Storage Fusion Global Data Platform and IBM Storage Scale Container Storage Interface
Driver are deployed on the worker nodes of your OpenShift cluster.
```
▾ IBM Storage Scale Container Native storage
IBM Storage Scale Container Native connects to your IBM Storage Scale Storage Cluster through a

- You can use dedicated storage nodes.
- Your storage nodes can co-exist with your worker nodes.


remote network mount to provide access to the high-performance General Parallel File System (GPFS).
IBM Storage Scale Container Native provides persistent data storage through the IBM Storage Scale
Container Storage Interface Driver.

Both IBM Storage Scale Container Native and IBM Storage Scale Container Storage Interface Driver are
deployed on the worker nodes of your OpenShift cluster.

▾ Portworx storage
If you are using Portworx storage, you must add raw disks on the OpenShift _worker_ nodes that you
intend to use for storage. (These can be the same nodes as the worker nodes where you run services.)
When you install Portworx on your cluster, the Portworx service will take over those disks automatically
and use them for dynamic storage provisioning.

▾ NFS storage
If you are using NFS storage, you can use either of the following configurations:

▾ AWS with EFS storage only
Amazon Elastic File System storage is external to the Cloud Pak for Data cluster. With this storage
option, you must use the EFS provisioner to connect to your AWS environment that has the Amazon
Elastic File System storage.

▾ AWS with EFS and EBS storage
Amazon Elastic File System storage is external to the Cloud Pak for Data cluster. With this storage
option, you must use the EFS provisioner to connect to your AWS environment that has the Amazon
Elastic File System storage.

If you're also using Amazon Elastic Block Store storage, use the EBS CSI driver that is automatically
provisioned as part of your AWS cluster to connect to your AWS environment.

▾ NetApp Trident storage

**Self-managed NetApp Trident**

```
You can use an external NFS server. In this configuration, you must have a sufficiently fast network
connection to reduce latency and ensure performance.
```
## –

- You can install NFS on a dedicated node in the same VLAN as the cluster.


```
NetApp Trident storage is external to the Cloud Pak for Data cluster. With this storage option, the
NetApp Trident operator is installed on the Cloud Pak for Data cluster. This operator connects to a
remote server that has the NetApp Trident storage.
```
**Managed NetApp Trident (Amazon FSx for NetApp ONTAP)**

```
NetApp Trident storage is external to the Cloud Pak for Data cluster. With this storage option, the
NetApp Trident operator is installed on the Cloud Pak for Data cluster. This operator connects to the
Amazon FSx for NetApp ONTAP file system.
```
```
Parent topic:
Architecture for IBM Cloud Pak for Data
```

