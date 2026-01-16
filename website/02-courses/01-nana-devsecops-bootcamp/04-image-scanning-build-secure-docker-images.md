---
layout: page
title: Techworld with Nana - DevSecOps Bootcamp - Image Scanning - Build Secure Docker Images
description: Techworld with Nana - DevSecOps Bootcamp - Image Scanning - Build Secure Docker Images
keywords: courses, Techworld with Nana - DevSecOps Bootcamp - Image Scanning - Build Secure Docker Images
permalink: /courses/devsecops/nana-devsecops-bootcamp/image-scanning-build-secure-docker-images/
---

# [Techworld with Nana] DevSecOps Bootcamp [2024, ENG]: Image Scanning - Build Secure Docker Images

<br/>

**Делаю:**  
2026.01.16

<br/>

Ерунда какая-то. Нужно сначала проверить, а потом пушить в registry. Пока переделывать не хочется.

<br/>

**.gitlab-ci.yml**

<br/>

```yaml
variables:
  IMAGE_NAME: webmakaka/demo-app
  IMAGE_TAG: juice-shop-$CI_COMMIT_SHA

stages:
  - build

build_image:
  stage: build
  image: docker:24.0.5
  services:
    - name: docker:24.0.5-dind
      command: ['--tls=false']
  variables:
    DOCKER_HOST: tcp://localhost:2375
    DOCKER_TLS_CERTDIR: ''

  before_script:
    - |
      for i in $(seq 1 30); do
        if nc -z localhost 2375; then
          echo "Docker is up and running!"
          break
        fi
        echo "Waiting for Docker daemon..."
        sleep 1
      done
    - echo $DOCKER_PASS | docker login -u $DOCKER_USER --password-stdin
  script:
    - docker build -t $IMAGE_NAME:$IMAGE_TAG .
    - docker push $IMAGE_NAME:$IMAGE_TAG

trivy:
  stage: build
  needs: ['build_image']
  image: docker:24.0.5
  services:
    - name: docker:24.0.5-dind
      command: ['--tls=false']
  variables:
    DOCKER_HOST: tcp://localhost:2375
    DOCKER_TLS_CERTDIR: ''
  before_script:
    - |
      for i in $(seq 1 30); do
        if nc -z localhost 2375; then
          echo "Docker is up and running!"
          break
        fi
        echo "Waiting for Docker daemon..."
        sleep 1
      done
    - echo $DOCKER_PASS | docker login -u $DOCKER_USER --password-stdin
    - apk --no-cache add curl
    - curl -sfL https://raw.githubusercontent.com/aquasecurity/trivy/main/contrib/install.sh | sh -s -- -b /usr/local/bin
  script:
    - docker pull $IMAGE_NAME:$IMAGE_TAG
    - trivy image -f json -o trivy.json --severity HIGH,CRITICAL --exit-code 1 $IMAGE_NAME:$IMAGE_TAG
  allow_failure: true
  artifacts:
    when: always
    paths:
      - trivy.json
```
