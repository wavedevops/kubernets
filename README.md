# command 
## 1. Create a pod
```bash
kubectl run prasad --image=docker.io/nginx
````

* **Pod name:** `prasad`  **Image:** `nginx`

---

## 2. List all pods in the cluster

```bash
kubectl get pods
```

```commandline
➜  ~ kubectl get pods
NAME     READY   STATUS    RESTARTS   AGE
prasad   1/1     Running   0          8s
```

---

## 3. List pods in a particular namespace

```bash
kubectl get pods -n prasad
```

```commandline
➜  kubernets kubectl get pods -n prasad
NAME     READY   STATUS    RESTARTS   AGE
nginx    1/1     Running   0          45h
prasad   1/1     Running   0          7m32s
```
---
## yaml in kubernetes
```yaml
apiVersion:       # version of api     `string`                  
kind:             # type of object     `string`
metadata:        # metadata is data. data about the object line name , labels ext   `map or Dictionary`
spec:
```
```shell
kubectl port-forward svc/frontend 8080:80 -n prasad
```
```terminaloutput
 4131  docker build -t chandrahari296/ubuntu-systemd-demo:latest
 4150  docker push chandrahari296/ubuntu-systemd-demo:latest
```
```yaml
apiVersion: apps/v1
kind: ReplicaSet
metadata:
  name: myapp-replicaset
  labels:
    app: myapp          # labeling the ReplicaSet itself
spec:
  replicas: 3
  selector:
    matchLabels:
      role: front-end   # MUST match pod template
  template:
    metadata:
      labels:
        app: myapp
        role: front-end  # pod label that matches selector
    spec:
      containers:
      - name: nginx-container
        image: nginx:latest
        ports:
        - containerPort: 80
```
```shell
# ✅ Create the ReplicaSet from YAML
kubectl create -f replicaset-definition.yml

# 🔁 Scale using the YAML file (to 6 replicas)
kubectl scale --replicas=6 -f replicaset-definition.yml

# 🔁 Scale using the resource name (to 6 replicas)
kubectl scale --replicas=6 replicaset myapp-replicaset

# 🔽 Scale down to 4 replicas
kubectl scale --replicas=4 replicaset/myapp-replicaset

# 🔼 Scale up to 6 replicas
kubectl scale --replicas=6 replicaset/myapp-replicaset
```

### 🔍 Breakdown of  `type (replicaset)` and `name (myapp-replicaset)`

| Part               | Meaning                                                                 |
|--------------------|-------------------------------------------------------------------------|
| `replicaset`       | ✅ **Type** → This tells Kubernetes what kind of resource you're scaling. |
| `myapp-replicaset` | ✅ **Name** → This is the **name** of the specific ReplicaSet you're targeting. |
