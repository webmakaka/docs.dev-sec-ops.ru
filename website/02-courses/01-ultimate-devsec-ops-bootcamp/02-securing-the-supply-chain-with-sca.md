---
layout: page
title: Ultimate DevSecOps Bootcamp by School of Devops - Securing the Supply Chain with SCA
description: Ultimate DevSecOps Bootcamp by School of Devops - Securing the Supply Chain with SCA
keywords: courses, Ultimate DevSecOps Bootcamp by School of Devops, Securing the Supply Chain with SCA
permalink: /courses/devsecops/ultimate-devsec-ops-bootcamp/securing-the-supply-chain-with-sca/
---

# Ultimate DevSecOps Bootcamp by School of Devops: Securing the Supply Chain with SCA

<br/>

**Делаю:**  
2025.12.26

<br/>

Проверка на лицензии

<br/>

```
    stage('Static Analysis') {
      parallel {
        stage('Unit Tests') {
          steps {
            container('maven') {
              sh 'mvn test'
            }
          }
        }

        stage('SCA') {
            steps {
                container('maven') {
                    catchError(buildResult: 'SUCCESS', stageResult: 'FAILURE') {
                        sh 'mvn org.owasp:dependency-check-maven:check'
                    }
                }
            }
            post {
                always {
                    archiveArtifacts(
                        allowEmptyArchive: true,
                        artifacts: 'target/dependency-check-report.html',
                        fingerprint: true,
                        onlyIfSuccessful: true
                        )
                    // dependencyCheckPublisher pattern: 'report.xml'
                }
            }
        }

        stage('OSS License Checker') {
            steps {
                container('licensefinder') {
                    sh 'ls -al'
                    sh '''#!/bin/bash --login
                        /bin/bash --login
                        rvm use default
                        gem install license_finder
                        license_finder
                    '''
                }
            }
        }

      }
    }
```
