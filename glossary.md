# oVirt Glossary (Terminology)

<!-- MarkdownTOC -->

- [Host](#host)
- [Self-Hosted Engine](#self-hosted-engine)
- [Data Centers](#data-centers)
- [Clusters](#clusters)
- [VDSM](#vdsm)
- [MoM](#mom)
- [Virtual Machine Pool](#virtual-machine-pool)
- [Storage Domains](#storage-domains)
- [Networks](#networks)
- [Datacenter Networks](#datacenter-networks)
- [vNIC Profiles](#vnic-profiles)
- [External Providers](#external-providers)
- [Node](#node)

<!-- /MarkdownTOC -->


<a name="host"></a>
### Host

The (physical) server runs oVirt / KVM and on which virtual machines run.

[https://www.ovirt.org/documentation/admin-guide/chap-Hosts/](https://www.ovirt.org/documentation/admin-guide/chap-Hosts/)


<a name="self-hosted-engine"></a>
### Self-Hosted Engine

A self-hosted engine is a virtualisation environment in which the oVirt Engine runs on a virtual machine on the hosts managed by that engine.

- The virtual machine is created as part of the host configuration, and the Engine is installed and configured in parallel to the host configuration process.
- The Engine is configured to be highly available, if the host running the Engine virtual machine goes into maintenance mode, or fails unexpectedly, the virtual machine will be migrated automatically to another host in the environment.


<a name="data-centers"></a>
### Data Centers

Think of it like a site that contains a group of resources.

- A data center is a logical entity that defines the set of resources used in a specific environment.
- A data center is considered a container resource, in that it is comprised of logical resources, in the form of clusters and hosts; network resources, in the form of logical networks and physical NICs; and storage resources, in the form of storage domains.
- A data center can contain multiple clusters, which can contain multiple hosts; it can have multiple storage domains associated to it; and it can support multiple virtual machines on each of its hosts. An oVirt environment can contain multiple data centers; the data center infrastructure allows you to keep these centers separate.

[https://www.ovirt.org/documentation/admin-guide/chap-Data_Centers/](https://www.ovirt.org/documentation/admin-guide/chap-Data_Centers/)

<a name="clusters"></a>
### Clusters

A cluster is a logical grouping of hosts that share the same storage domains and have the same type of CPU (either Intel or AMD).

- If the hosts have different generations of CPU models, they use only the features present in all models.
- Each cluster in the system must belong to a data center, and each host in the system must belong to a cluster.
- Virtual machines are dynamically allocated to any host in a cluster and can be migrated between them, according to policies defined on the Clusters tab and in the Configuration tool during runtime.
- The cluster is the highest level at which power and load-sharing policies can be defined.


<a name="vdsm"></a>
### VDSM

"Virtual Desktop and Server Manager"

- Vdsm manages and monitors the host's storage, memory and networks as well as virtual machine creation, other host administration tasks, statistics gathering, and log collection.
- Vdsm exclusive write access to libvirt. NO OTHER PROCESS should be using libvirt on a Vdsm host.

[https://www.ovirt.org/develop/developer-guide/vdsm/vdsm/](https://www.ovirt.org/develop/developer-guide/vdsm/vdsm/)

<a name="mom"></a>
### MoM

"Memory Overcommit Manager"

- MOM keeps track of active virtual machines on a host
- MOM is a policy-driven tool that can be used to manage overcommitment on KVM hosts.

[https://www.ovirt.org/develop/projects/mom/](https://www.ovirt.org/develop/projects/mom/)


<a name="virtual-machine-pool"></a>
### Virtual Machine Pool

- A virtual machine pool is a group of virtual machines that are all clones of the same template and that can be used on demand by any user in a given group.
- Virtual machine pools allow administrators to rapidly configure a set of generalised virtual machines for users.

[https://www.ovirt.org/documentation/admin-guide/chap-Pools/](https://www.ovirt.org/documentation/admin-guide/chap-Pools/)


<a name="storage-domains"></a>
### Storage Domains

A storage domain is a collection of images that have a common storage interface.

- A storage domain contains complete images of templates and virtual machines (including snapshots), or ISO files.
- A storage domain can be made of either block devices (SAN - iSCSI or FCP) or a file system (NAS - NFS, GlusterFS, or other POSIX compliant file systems).

[https://www.ovirt.org/documentation/install-guide/chap-Configuring_Storage/](https://www.ovirt.org/documentation/install-guide/chap-Configuring_Storage/)

<a name="networks"></a>
### Networks

In order to be able to actually use the network, you must attach it to the cluster first. Once a network is attached to the cluster, you can use it in VMs and templates, and set it up on the hosts.

Networking in oVirt comprises of several layers:

- The logical network definition (Data center + cluster network)
- The actual implementation (The host level)
- The usage of the network (vNIC profiles + vNICs)

<a name="datacenter-networks"></a>
### Datacenter Networks

- The first and foremost container of a network is the data center.
- The data center's networks are modelled under the data center (in the system tree and main tabs).
- In this scope, each network must have a unique name and a unique VLAN tag (if it's used).


<a name="vnic-profiles"></a>
### vNIC Profiles

The VNIC Profile concept embodies a predefined package of network setting which will define the network service a vNIC will get.

- Network
- Quality of Service
- Port mirroring
- Custom properties


[https://www.ovirt.org/develop/release-management/features/sla/vnic-profiles/](https://www.ovirt.org/develop/release-management/features/sla/vnic-profiles/)

<a name="external-providers"></a>
### External Providers

In addition to resources managed by the oVirt Engine itself, oVirt can also take advantage of resources managed by external sources.

- The providers of these resources, known as external providers, can provide resources such as virtualization hosts, virtual machine images, and networks.


<a name="node"></a>
### Node

Infoxchange is _not_ using oVirt Node.

- oVirt node is a custom distro based on CentOS with oVirt pre-installed
