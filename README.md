### OCS/ODF | Storage Cluster Deployment with ArgoCD

#### About
This repository contains two top level directories each with a group of
Kustomize manifests to fullfill the these very high level goals:

* Deploy an ArgoCD instance in an OpenShift Container Platform(OCP) cluster
* Deploy an OpenShift Container Storage(OCS)/OpenShift Data Foundation(ODF) cluster 
using a declarative Continous Delivery(CD) tooling such as ArgoCD. 

The motivation for this repository is to provide functional example of  
automated deployment of an OCS/ODF cluster using a K8s declarative approach with 
tooling such as ArgoCD and including the basic installation of the ArgoCD framework.
The manifests on this repository comes from a loose fork of this repository <https://github.com/tkagn/ocp4gitops-public>. 
Credit goes to @tkagn for the inspiration.

#### Platform and Versions Tested
* OpenShift Container Platform 4.8 deployed via OpenStack/UPI
* OpenShift Container Storage(4.8-stable) 
* Local Storage Operator(stable)

#### Assumptions
* This repository provides working examples and assumes that you have some
exposure to Kubernetes and OpenShift platforms.
* Familiar with the OpenShift Operators concepts.
* Familiarity with ArgoCD, and Kustomize templates.
* You have exposure and/or experience in OCS/ODF.
* You have a technical reason or curiosity to have an automated deployment of
OCS/ODF using a continous delivery method.

#### Disclaimers
* While functional, these manifests will need refactoring to adhere to
your site specific Gitops practices. 
* These code and/or manifests are not supported by Red Hat and are provided to
the open source community as a way to share learning experiences.
* Take this and make it your own. I'd love to hear if it helped you in some way.

#### Repository Structure
```
ocs4argocd/
├── acd-managed-applications  #<---- OCS ArgoCD Managed Applications
│   ├── dev-ocs-cluster
│   │   ├── kustomization.yaml
│   │   ├── lso-application.yaml
│   │   ├── ocso-application.yaml
│   │   └── storagecluster-application.yaml
│   ├── lso                   #<---- Local Storage Operator Deployment Application
│   │   ├── kustomization.yaml
│   │   ├── lso-auto-discovery.yaml
│   │   ├── lso-namespace.yaml
│   │   ├── lso-ocs-volumeset.yaml
│   │   ├── lso-operator-group.yaml
│   │   └── lso-subscription.yaml
│   ├── ocso                  #<---- OpenShift Container Storage Operator Application
│   │   ├── kustomization.yaml
│   │   ├── ocs-namespace.yaml
│   │   ├── ocs-operator-group.yaml
│   │   └── ocs-subscription.yaml
│   └── storagecluster        #<---- Ceph Storage Cluster Application
│       ├── cephblockpool-r2.yaml
│       ├── kustomization.yaml
│       ├── ocs-storage-cluster.yaml
│       └── storageclass-rbd-r2.yaml
├── acd-operator-deployment   #<---- ArgoCD Deployment Application
│   ├── argocd-cluster.yaml
│   ├── argocd-kustomize-build-options-cm.yaml
│   ├── argocd-rbac-cm.yaml
│   ├── cluster-role-binding-argocd.yaml
│   ├── dev-ocs-infra-application.yaml
│   ├── dev-ocs-infra-project.yaml
│   ├── kustomization.yaml
│   ├── namespace-argocd.yaml
│   ├── operatorgroup-argocd.yaml
│   └── subscription-argocd.yaml
├── LICENSE
└── README.md
```

#### Relevant Documentation
* [Red Hat OpenShift Container Storage 4.8 Documetation:](https://access.redhat.com/documentation/en-us/red_hat_openshift_container_storage/4.8)
* [ArgoCD Documentation](https://argo-cd.readthedocs.io/en/stable/)
* [Kustomize Native Configuration Management](https://kustomize.io/)
