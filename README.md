# sample-k8s-jenkins

A sample configuration for Jenkins on Kubernetes. This sample is tested on Minikube for Mac.

## Usage

Create a namespace `jenkins`:

```
kubectl create namespace jenkins
```

Create a persistent volume used as `JENKINS_HOME`:

```
kubectl create -f pv.yaml
```

Create a stateful set and a service for Jenkins:

```
kubectl create -f statefulset.yaml
```

(Optional) Create a servivce for Jenkins agents:

```
kubectl create -f service-agent.yaml
```

Create a pod getting the initial admin password to unlock Jenkins after the statefulset launched:

```
kubectl create -f initial-admin-password.yaml
```

Get the initial admin password:

```
kubectl --namespace=jenkins logs initial-admin-password
```

and copy its result.

Open Jenkins UI with Minikube:

```
minikube service -n=jenkins jenkins
```

Paste the initial admin password into the unlock page.
