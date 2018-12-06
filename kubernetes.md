## Glossary

cluster: 1 "master" and N nodes where you "run" an application

node: a machine (physical or VM) in a cluster. It talks to the master via the kubernetes API. Serves as a "worker"

master: schedules applications on nodes in the cluster, maintains state?

deployment: how to create and update your app instances. kubernetes will try to self-heal and monitor. Requires a _container image_ 

pod: a group of one or more application containers and shared resources like Volumes, Networking, metadata


## Commands

`kubectl version`: client and server versions. Not sure how kubectl knows what cluster to use..

`kubectl cluster-info`

`kubectl run`

`kubectl get node`