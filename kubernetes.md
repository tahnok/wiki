## Glossary

cluster: 1 "master" and N nodes where you "run" an application

node: a machine (physical or VM) in a cluster. It talks to the master via the kubernetes API. Serves as a "worker". Can host one or more pods. Runs "kubelet" that allows the master to talk to it.

master: schedules applications on nodes in the cluster, maintains state?

deployment: how to create and update your app instances. kubernetes will try to self-heal and monitor. Requires a _container image_ 

pod: a group of one or more application containers and shared resources like Volumes, Networking, metadata. Like a physical host of old, shares an IP address and port space and run on a single node together

scheduling: the thing the master does to decide which nodes to run a pod on

resources: a deployment or a service or a volume. Maybe like objects?

service: a set of pods defined by selectors that are exposed via a mechanism like an cluster internal IP, or a load balancer. Used to facilitate inter-cluster communication without depending on a particular pod. (ie mysql service, not host123 that is running mysql)

selector: a way to define which labels to look for in a service?

label: a key/value pair attached to an object (a pod, but what else?)

replica: number of pods requested in a deployment. Can be turned up or down and it will automatically schedule new pods. Will automatically balance a service across all pods in a replica (as defined by a label? or a deployment?)


rollout: tool used to monitor updates to containers (as new pods are created)

namespace: a way to partition pods, services while running on the same "cluster". Nodes and persistentVolumes are _not_ namespaced

workload: a pod or a controller. Runs on nodes

controllers: a thing not a pod that lives in kubernetes. Includes deployments, ReplicaSet and Jobs

jobs: one or more pods that runs and then terminates.

[[/kubernetes/module_03_nodes.svg]]

## Commands

`kubectl version`: client and server versions. Not sure how kubectl knows what cluster to use..

`kubectl cluster-info`

`kubectl run`

`kubectl get node`

## references

[[https://kubernetes.io/docs/tutorials/kubernetes-basics/]]