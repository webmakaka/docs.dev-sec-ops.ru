---
layout: page
title: Ultimate DevSecOps Bootcamp by School of Devops - Auditing Container Images
description: Ultimate DevSecOps Bootcamp by School of Devops - Auditing Container Images
keywords: courses, Ultimate DevSecOps Bootcamp by School of Devops, Auditing Container Images
permalink: /courses/devsecops/ultimate-devsecops-bootcamp/auditing-container-images/
---

# Ultimate DevSecOps Bootcamp by School of Devops: Auditing Container Images

<br/>

**Делаю:**  
2026.01.02

<br/>

Сканируем docker image на уязвимости и Dockerfile на их корректность с т.з. безопасности.

<br/>

```
stage('Image Analysis') {
    parallel {
        stage('Image Linting') {
            steps {
                container('docker-tools') {
                    sh 'dockle webmakaka/dso-demo --exit-code 1'
                }
            }
        }
        stage('Image Scan') {
            steps {
                container('docker-tools') {
                    sh 'trivy image --exit-code 1 webmakaka/dso-demo'
                }
            }
        }
    }
}
```

<br/>
