# Basic K8s overview
- Your application runs in a docker container, which is generated from an image created from a Dockerfile.
- A group of intimately related containers runs in a Pod. Pods most often have just one container. Each Pod is generally one application. 
- A Service object is an abstract way of making pods available for networking. A service will direct requests to the appropriate pods, provide an internal address for private pods, and can provision a load balancer to expose pods to outside requests. Within the cluster, you can access a service's pods by sending requests to SERVICE_NAME.NAMESPACE.svc.cluster.local. Outside the cluster, a load balanced service can be reached at SERVICE_NAME.NAMESPACE.cloud.exo-imaging.com.
- A Deployment object manages pods, and aims to ensure there are a specified number of pods from a particular template running and healthy. Generally, all pods will be created by deployments, and you bring up new versions of pods by updating the deployment object, so it will gradually replace them.
- Nodes are the servers (ec2 instances) that stuff runs on. You don't really have to worry about them.
- We use helm packages (called charts) to create and manage groups of associated services and deployments, and their configurations and dependencies. The chart for an application will be located in a directory of the application's name, in the root of the repository.

A fantastic resource for debugging problems with getting your application running properly is https://kubernetes.io/docs/tasks/debug-application-cluster/debug-application/ and it is worth reading over it once and then using it as a reference. If you're only going to remember one bit of debugging advice, check the logs.

Highly useful tools:
[Stern](https://github.com/wercker/stern) makes it very easy to get the logs of multiple pods and see the logs as you repeatedly deploy new versions of the same code.
[Kubectx/kubens](https://github.com/ahmetb/kubectx) make switching between clusters and namespaces much easier/faster.
