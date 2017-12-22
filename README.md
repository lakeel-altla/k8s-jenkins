# sample-k8s-jenkins

A sample configuration for Jenkins on Kubernetes.

## Usage

Create a namespace `jenkins`.

```
kubectl create namespace jenkins
```

Create a persistent volume used as `JENKINS_HOME`.

```
kubectl create -f pv.yaml
```

Create a stateful set and a service for Jenkins.

```
kubectl create -f statefulset.yaml
```

(Optional) Create a servivce for Jenkins agents.

```
kubectl create -f service-agent.yaml
```

SSH to minikube.

```
minikube ssh
```

Cat `initialAdminPassword`:

```
sudo cat /var/jenkins_home/secrets/initialAdminPassword
```

and copy its result.

Open the Jenkins UI.

```
minikube service -n jenkins jenkins
```

Paste the value of `initialAdminPassword`.
