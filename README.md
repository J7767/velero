# velero
Velero, Backup OpenShift Resources the Native Way
( https://blog.openshift.com/backup-openshift-resources-the-native-way/  )

The age old question from an operations perspective is: ‘Do we have a backup strategy for the company?’  If the answer is yes, then we would also ask ‘does that strategy include accommodations for emerging technologies such as Kubernetes?’ We believe this question comes to bear in a couple of different ways when it pertains to Kubernetes native infrastructure such as Red Hat OpenShift. In today’s day and age of cloud computing, the pervasive answer is to recreate. However, every organization does not always have the strategy to recreate the resources fresh and new. We believe there is a mix of “recreate new” versus “backup and restore.” One such option comes to mind, and that is an open source project call velero. Velero is a project started by a company called Heptio, recently purchased by Dell/VMware, that is capable of backing up all the resources of a project as well as backing up the persistent storage used by the applications. For the duration of the article we will focus on the implementation of that solution and what it looks like in a practical way using examples from a real cluster. A word of caution to the reader: Velero has a support matrix that correlates to a minimum version of Kubernetes, which can be found here.
Architecture
Our architecture is a client-server based setup. As we progress through this document we will explore how to setup the environment with all the needed components as well as show you how to create a backup of a project/namespace and restore that very backup to the same cluster, but it could easily target another cluster.
 <
Prerequisites
Now let’s move to the install phases. Velero as a solution has some prerequisites for installation and configuration as you will see listed below. For the purposes of this article we will assume an OpenShift Cluster is used as the primary platform to install and run our Velero and S3 compatible components.
•	Must have an OCP cluster >= 3.7 (Due to the CRD support requirement).
•	Logged in as a cluster-admin to configure all the components.
•	S3-Compatible Object store. 
o	In our examples we show you how to install minio, an S3 compatible object store, as well as how to install and use an AWS S3 object store.
 

