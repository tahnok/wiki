## Glossary

cluster: 1 "master" and N nodes where you "run" an application

node: a machine (physical or VM) in a cluster. It talks to the master via the kubernetes API. Serves as a "worker". Can host one or more pods. Runs "kubelet" that allows the master to talk to it.

master: schedules applications on nodes in the cluster, maintains state?

deployment: how to create and update your app instances. kubernetes will try to self-heal and monitor. Requires a _container image_ 

pod: a group of one or more application containers and shared resources like Volumes, Networking, metadata. Like a physical host of old, shares an IP address and port space and run on a single node together

scheduling: the thing the master does to decide which nodes to run a pod on

resources: ??

replication controller: ?? 

service: a set of pods defined by selectors that are exposed via a mechanism like an cluster internal IP, or a load balancer. Used to facilitate inter-cluster communication without depending on a particular pod. (ie mysql service, not host123 that is running mysql)

selector: a way to define which labels to look for in a service?

label: a key/value pair attached to an object (a pod, but what else?)



[[/kubernetes/module_03_nodes.svg]]

## Commands

`kubectl version`: client and server versions. Not sure how kubectl knows what cluster to use..

`kubectl cluster-info`

`kubectl run`

`kubectl get node`