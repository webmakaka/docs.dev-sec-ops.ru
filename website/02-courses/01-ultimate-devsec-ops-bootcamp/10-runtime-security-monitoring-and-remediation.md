---
layout: page
title: Инсталляция Jenkins в ubuntu 22.04
description: Инсталляция Jenkins в ubuntu 22.04
keywords: tools, containers, kubernetes, ci-cd, Jenkins, инсталляция
permalink: /courses/devsecops/ultimate-devsecops-bootcamp/runtime-security-monitoring-and-remediation/
---

# Runtime Security Monitoring and Remediation

<br/>

**Делаю:**  
2026.01.05

<br/>

https://artifacthub.io/packages/helm/falcosecurity/falco

<br/>

```
$ helm repo add falcosecurity https://falcosecurity.github.io/charts
$ helm repo update
```

<br/>

```
$ helm install falco falcosecurity/falco \
    --create-namespace \
    --namespace falco
```

<br/>

```
$ kubectl get pods -n falco
NAME          READY   STATUS    RESTARTS   AGE
falco-dlz65   2/2     Running   0          5m19s
```

<br/>

```
$ kubectl get pods -n falco
NAME          READY   STATUS    RESTARTS   AGE
falco-dlz65   2/2     Running   0          5m19s
```

<br/>

```
$ kubectl logs falco-dlz65 -n falco
```

<br/>

Создали файл с правилами для приложения.

<br/>

```
$ helm upgrade -n falco falco -f custom-rules.yaml falcosecurity/falco
```

<br/>

https://github.com/lfs262/argo-falco/blob/master/install.sh

<br/>

```
$ cd ~/tmp
$ git clone https://github.com/wildmakaka/argo-falco.git
$ cd argo-falco
```

<br/>

Разкомментировал все, что касается falco

```
$ ./install.sh
```

<br/>

Нужно развернуть приложение dso-demo в namespace dev

<br/>

```
$ kubectl create ns dev
```

<br/>

<br/>

**dso-demo-deploy.yaml**

```yaml
$ cat << 'EOF' | kubectl create -f -
apiVersion: apps/v1
kind: Deployment
metadata:
  creationTimestamp: null
  namespace: dev
  labels:
    app: dso-demo
  name: dso-demo
spec:
  replicas: 1
  selector:
    matchLabels:
      app: dso-demo
  strategy: {}
  template:
    metadata:
      creationTimestamp: null
      labels:
        app: dso-demo
    spec:
      containers:
        - image: webmakaka/dso-demo
          name: dso-demo
          ports:
            - containerPort: 8080
          resources: {}
status: {}
EOF
```

<br/>

**dso-demo-svc.yaml**

```yaml
$ cat << 'EOF' | kubectl create -f -
apiVersion: v1
kind: Service
metadata:
  creationTimestamp: null
  namespace: dev
  labels:
    app: dso-demo
  name: dso-demo
spec:
  ports:
    - name: '8080'
      nodePort: 30080
      port: 8080
      protocol: TCP
      targetPort: 8080
  selector:
    app: dso-demo
  type: NodePort
status:
  loadBalancer: {}
EOF
```

<br/>

```
$ kubectl scale deploy dso-demo -n dev --replicas=2
```

<br/>

```
$ kubectl get pods -n dev
NAME                        READY   STATUS    RESTARTS   AGE
dso-demo-794d8d5d9f-dzxp9   1/1     Running   0          2m13s
dso-demo-794d8d5d9f-xgbmv   1/1     Running   0          49s
```

<br/>

```
// Должен pod удаляться
// Но у меня ничего не происходит
$ kubectl exec -it -n dev dso-demo-794d8d5d9f-dzxp9 -- sh
```

<br/>

```
$ kubectl get pods -n argo
NAME                                  READY   STATUS    RESTARTS   AGE
argo-server-767bbbfb8d-shmb7          1/1     Running   0          49m
workflow-controller-9749bbdc5-qpc7g   1/1     Running   0          49m
```
