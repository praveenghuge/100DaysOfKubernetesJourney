# Kubernetes Architecture

Kubernetes Components
    - Control Plane
    - Nodes (Worker Nodes)
    
    ![image](https://user-images.githubusercontent.com/33432891/226561396-e5181d2c-b5fe-4920-af48-96e1654cd5cb.png)

## Introduction

Control Plane - make global decisions about the cluster(for eg, scheduling, respond to events)


Components : 

    - kube-apiserver: exposes kubernetes API, works as a frontend to kubernetes
    
    - etcd: consistent and highly available key-value store, backing store for all cluster data.
    
    - kube-schedular: (watcher) - takes scheduling decisions based on several factors, individual and collective resources reqs, hardware/software constraints, affinity and anti-affinity specifications, data locality, inter-workload interference and deadlines.
    
    - kube-controller-manager: 
        - node-controller: responsible for noticing and responding when the nodes go down.
        - job controller: watches jobs objs that represents one-off tasks, then creates pods to run those tasks competition.
        - endpointSlice controller: populates EndpointSlice objects (to provide the link between services and pods).
        - serviceaccount-controller: creates default serviceaccounts for new namespaces.
        
    - cloud-controller-manager: embeds cloud specific control logic. The cloud controller manager lets you link your cluster into your cloud provider API and separate out the components that interacts with that cloud platform from components that only interacts with cluster.
        - node controller: for checking the cloud provider to determine if a node has been deleted in the cloud after it stops responding.
        - route controller: for setting up routes in the underlying cloud infrastructure.
        - service controller: for creating, updating and deleting cloud load balancers.

#Kubernetes Architecture 

Nodes: Worker Nodes

- A Kubernetes cluster consists of a set of worker machines, called nodes, that run containerized applications. Every cluster has at least one worker node.

Components:
    - kubelet: An agent that runs on each node. It makes sure that container are running in Pod.
        checks PodSpecs --> running and healthy.
    - kubeproxy: implements kubernetes service concepts on each node. maintain network rule book on nodes.
        network rule book allows communication between pods from inside and outside
    - container runtime(*): software responsible for running containers.
        -- https://github.com/kubernetes/community/blob/master/contributors/devel/sig-node/container-runtime-interface.md

ADDOns:
    - (daemonset, deployments), providing cluster level feature are part of kube-system namespace
        https://kubernetes.io/docs/concepts/cluster-administration/addons/

    - DNS: serves DNS records for kubernetes services.
        containers started by kubernetes automatically include the DNS servers in the DNS searches
    
    - WebUI: dashboard

    - Container resource monitoring: time-series metrics about containers in a centralized database https://kubernetes.io/docs/tasks/debug/debug-cluster/resource-usage-monitoring/

    - Cluster level logging: mechanism is responsible for saving container logs at central log store with search/browsing interface https://kubernetes.io/docs/concepts/cluster-administration/logging/

    

## Prerequisite


## Use Case


## Research
https://kubernetes.io/docs/concepts/overview/components/

TODO: https://kubernetes.io/docs/setup/production-environment/tools/kubeadm/high-availability/


## Try yourself
