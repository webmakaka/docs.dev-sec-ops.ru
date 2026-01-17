---
layout: page
title: DevSecOps with GitLab - Secure CI/CD with GitLab
description: DevSecOps with GitLab - Secure CI/CD with GitLab
keywords: courses, DevSecOps with GitLab - Secure CI/CD with GitLab
permalink: /courses/devsecops/secure-ci-cd-with-gitlab/
---

# [Udemy] DevSecOps with GitLab - Secure CI/CD with GitLab [2024, ENG]

<br/>

https://github.com/asecurityguru/devsecops-gitlab-java-vulnerable-application

https://github.com/asecurityguru/devsecops-gitlab-simple-ci-yml-file-repo

<br/>

## 04 - Implement SAST in GitLab DevSecOps Pipeline using SonarCloud

<br/>

### 003 Hands-On Integrate SonarCloud within GitLab DevSecOps pipeline

https://github.com/asecurityguru/devsecops-gitlab-sonarcloud-sast-without-code-coverage-repo

<br/>

```yaml
stages:
  - runSAST

run-sast-job:
  stage: runSAST
  image: maven:3.8.5-openjdk-17-slim
  script: |
    mvn verify package sonar:sonar -Dsonar.host.url=https://sonarcloud.io/ -Dsonar.organization=gitlabdevsecopsintegration -Dsonar.projectKey=gitlabdevsecopsintegration -Dsonar.token=token01
```

<br/>

### 004 Hands-On Create Quality Gates in DevSecOps pipeline using SonarCloud

```
1) Create Custom Quality Gate in SonarCloud and Add conditions to the Quality Gate
2) Assign this Quality Gate to the Project
3) Add script in .gitlab-ci.yml file to enable quality gate check (Note: This will fail your build in case Quality Gate fails)

sleep 5
apt-get update
apt-get -y install curl jq
quality_status=$(curl -s -u 14ad4797c02810a818f21384add02744d3f9e34d: https://sonarcloud.io/api/qualitygates/project_status?projectKey=gitLabdevsecopsintegration | jq -r '.projectStatus.status')
echo "SonarCloud Analysis Status is $quality_status";
if [[ $quality_status == "ERROR" ]] ; then exit 1;fi


-----------Sample JSON Response from SonarCloud or SonarQube Quality Gate API---------------------

{
	"projectStatus": {
		"status": "ERROR",
		"conditions": [
			{
				"status": "ERROR",
				"metricKey": "coverage",
				"comparator": "LT",
				"errorThreshold": "90",
				"actualValue": "0.0"
			}
		],
		"periods": [],
		"ignoredConditions": false
	}
}
```

<br/>

https://github.com/asecurityguru/devsecops-gitlab-sonarcloud-sast-with-quality-gates

<br/>

```yaml
stages:
  - runSAST

run-sast-job:
  stage: runSAST
  image: maven:3.8.5-openjdk-17-slim
  script: |
    apt-get update
    apt-get -y install curl jq
    mvn verify package sonar:sonar -Dsonar.host.url=https://sonarcloud.io/ -Dsonar.organization=gitlabdevsecopsintegrtion -Dsonar.projectKey=gitLabdevsecopsintegration -Dsonar.token=14ad4797c02810a818f21384add02744d3f9e34d
    sleep 5 
    quality_status=$(curl -s -u 14ad4797c02810a818f21384add02744d3f9e34d: https://sonarcloud.io/api/qualitygates/project_status?projectKey=gitLabdevsecopsintegration | jq -r '.projectStatus.status')
    echo "SonarCloud Analysis Status is $quality_status"; 
    if [[ $quality_status == "ERROR" ]] ; then exit 1;fi
```

<br/>

### 006 Hands-On Populate Unit Test Code Coverage on SonarCloud Dashboard for DevSecOps

```
1) Unit Test cases should be present in test folder
2) Junit Plugin should be present in pom.xml
3) Jacoco Plugin should be present in pom.xml
4) Jacoco report execution goal should be present in build tag in pom.xml
5) Maven "verify" goal should be run while running sonar analysis
```

<br/>

https://github.com/asecurityguru/devsecops-gitlab-sonarcloud-sast-with-code-coverage-repo
