# Sample Files for Kubeturbo Pod Deployment

### Overview
 [Kubeturbo](https://github.com/turbonomic/kubeturbo) leverages Turbonomic's patented analysis engine to provide visibility and control across the entire stack to assure the performance of running micro-services in Kubernetes Pods, as well as the efficiency of the underlying infrastructure.
 
 The files provided in this repo are aimed to provide a sample of working yamls that can be used to deploy all the resources needed.
 
 The repo includes six files:
  - All in one yaml that will create all the resources in one command (may not work on OpenShift) - please note this yaml includes new namespace creation
  - Five files are broken down into the order in which they should be deployed:
 NOTE: step 1-3 are optional if you wish to use an existing namespace and service account with admin-role permissions, if you choose this option, please make sure to update the configmap and deployment yamls with the relevant information.

 1_kubeturbo_namespace_SAMPLE.yml - this yaml will create a namespace (default name = turbo)
2_kubeturbo_serviceAccount_SAMPLE.yml - this yaml will create a serviceAccount (default name = turbo-user)
3_kubeturbo_serviceAccountRoleBinding_SAMPLE.yml - this yaml will create a role binding to a cluster-admin role
4_kubeturbo_ConfigMap_SAMPLE.yaml - this yaml includes an embedded JSON, you will need to update the JSON with the turbonomic address, version, and turbonomic admin credentials.
5_kubeturbo_deployment_SAMPLE.yml - this yaml includes all the details to deploy the pod including the container image to pull

 
 ### Assumptions:
 * You have admin level access to your Kubernetes deployment
 * You have kubectl installed
 * You have Turbonomic Server running

### How to use:

- Download the files to your computer
- Edit the files using a text editor, if you change a value, such as a namespace, please ensure to update all the respected sections in the following files
- Ensure you are connected to the right kubernetes cluster with the kubectl cli
- Use kubectl to create the resources

```sh
$ kubectl create -f <YAML FILE>
```
