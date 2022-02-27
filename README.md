# Learning Kubernetes

## KIND

Apply configuration to KIND cluster, including extra port mappings to expose LoadBalancer type services to the host on macOS and Windows hosts: <https://kind.sigs.k8s.io/docs/user/configuration/>.

Apply configuration to enable ingress and expose ports 80 and 443 to host: <https://kind.sigs.k8s.io/docs/user/ingress/>.

Install NGINX Ingress: <https://kind.sigs.k8s.io/docs/user/ingress/#ingress-nginx>.

Deploy Kubernetes Dashboard on KIND: <https://kubernetes.io/docs/tasks/access-application-cluster/web-ui-dashboard/>.

Generate service account, secrets and access token to be able to log into
Kubernetes dashboard:
<https://medium.com/@munza/local-kubernetes-with-kind-helm-dashboard-41152e4b3b3d>.

Make storage on local `hostPath` available for use in PV and pre-bind PVC to
this PV: 

* See `extraMounts` section in [kind-config-1.yaml](cluster-config/kind-config-1.yaml).
* See [mongo-pv.yaml](mongo-1/mongo-pv.yaml) and [mongo-pvc.yaml](mongo-1/mongo-pvc.yaml).
* Note that you have not made use of this PV in your mongo deployment. You would
  need to 
  * run the mongo container by specifying `dbpath` and setting the path of
  the data directory in the container (e.g., `/data/db`);
  * define a `volumeMount` with the data directory as the mount path;
  * define a `volume` that refers to your PVC.

## Basic kubectl commands

Create deployment: `kubectl create deployment <name> [options]`

Edit deployment: `kubectl edit deployment <name>`

Delete deployment: `kubectl delete deployment <name>`

Get status of different K8s components: `kubectl get nodes | pod | service | deployment | replicaset`

Get all components: `kubectl get all`

Get status and watch: `kubectl get pod --watch`

Get more status information: `kubectl get pod -o wide`

Get resource status from etcd as YAML: `kubectl get deployment nginx-deployment -o yaml`

Log to console: `kubectl logs <pod name>`

Get interactive terminal: `kubectl exec -it <pod name> -- bin/bash`

Get info about pod: `kubectl describe pod <pod name>`

Apply a configuration file: `kubectl apply -f <file name>`

Delete a resource with a configuration file: `kubectl delete -f <file name>`

Create a namespace: `kubectl create namespace <namespace name>`

Apply a configuration file to a specific namespace: `kubectl apply -f <file name> --namespace=<namespace name>`

`kubens` looks like a nice tool to be able to select an active namespace:

1.  `brew install kubectx`
2.  `kubens` or `kubens <namespace name>`
