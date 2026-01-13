---
layout: page
title: Ultimate DevSecOps Bootcamp by School of Devops - Подготовка оркужения
description: Ultimate DevSecOps Bootcamp by School of Devops - Подготовка оркужения
keywords: courses, Ultimate DevSecOps Bootcamp by School of Devops, Подготовка оркужения
permalink: /courses/devsecops/ultimate-devsecops-bootcamp/environment/
---

# [Gourav Shah] Ultimate DevSecOps Bootcamp by School of Devops [ENG, 2021]: Подготовка оркужения

<br/>

### [Инсталляция minikube](//docs.k8s.ru/tools/containers/kubernetes/minikube/setup/)

<br/>

### [Запуск и останов minikube в ubuntu 22.04](//docs.k8s.ru//tools/containers/kubernetes/minikube/run/)

<br/>

### Скачать image которые будут использовать заранее

```
$ eval $(minikube --profile ${PROFILE} docker-env)


$ {
    docker pull jenkins/inbound-agent:latest
    docker pull maven:3.8.6-openjdk-11
    docker pull gcr.io/kaniko-project/executor:v1.19.2-debug
    docker pull rmkanda/docker-tools:latest
    docker pull rmkanda/trufflehog:latest
    docker pull licensefinder/license_finder:latest
    docker pull shiftleft/sast-scan:latest
}
```

<br/>

### [Инсталляция jenkins в minikube](//docs.gitops.ru/courses/devsecops/ultimate-devsecops-bootcamp/setup/helm/minikube/)
