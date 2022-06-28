# serverless-stepfunction-workflows

This repository contains all the workflows.

## CICD

### Onboarding serverless-stepfunction-workflows onto exiting CICD pipeline: 
Note: all the steps in this section is based on this link: https://cicd.lifion.oneadp.com/docs/ci_onboarding

1. Run bash to initiate an exiting pipeline 

```
bash <(curl -k https://artifactory.us.caas.oneadp.com/artifactory/lifion-generic-local/CICD/ci-init-wizard/latest/init.sh)
```

The following output explains is what you could expect:

```
C02X50JRJGH8:serverless-stepfunction-workflows zhangson$ bash <(curl -k https://artifactory.us.caas.oneadp.com/artifactory/lifion-generic-local/CICD/ci-init-wizard/latest/init.sh)
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100  5687  100  5687    0     0  54150      0 --:--:-- --:--:-- --:--:-- 58628
Creating: '/Users/zhangson/Library/CloudStorage/OneDrive-AutomaticDataProcessingInc/Documents/ADP_Internship/Tickets/3_DEVOPS-6884/serverless-stepfunction-workflows/.build'
Writing:  '/Users/zhangson/Library/CloudStorage/OneDrive-AutomaticDataProcessingInc/Documents/ADP_Internship/Tickets/3_DEVOPS-6884/serverless-stepfunction-workflows/.build/bootstrap.sh'
Writing:  '/Users/zhangson/Library/CloudStorage/OneDrive-AutomaticDataProcessingInc/Documents/ADP_Internship/Tickets/3_DEVOPS-6884/serverless-stepfunction-workflows/.build/.gitignore'
Writing:  '/Users/zhangson/Library/CloudStorage/OneDrive-AutomaticDataProcessingInc/Documents/ADP_Internship/Tickets/3_DEVOPS-6884/serverless-stepfunction-workflows/Jenkinsfile'
Writing:  '/Users/zhangson/Library/CloudStorage/OneDrive-AutomaticDataProcessingInc/Documents/ADP_Internship/Tickets/3_DEVOPS-6884/serverless-stepfunction-workflows/.build/.ci.yml'
Which pipeline flavour?  Can be one of: custom' | 'packandpush' | 'docker' | 'serviceV2' | 'nodejsService' | 'npmServiceV2' | 'infraService' | 'npm' | 'dsl' | 'tf' | 'cloudformation' | 'pythonPip' | 'serverless
serviceV2
Writing:  '/Users/zhangson/Library/CloudStorage/OneDrive-AutomaticDataProcessingInc/Documents/ADP_Internship/Tickets/3_DEVOPS-6884/serverless-stepfunction-workflows/.build/.project.yml'
A docker image name has four parts registry/organisation/image:tag
e.g.
 - registry:     dockertr.es.ad.adp.com
 - organisation: ohcm_devops
 - repository:   nodejs-buildtools
 - tag:          latest
What is the organisation name? e.g. ohcm_devops
devops
What is the repository name? e.g. nodejs-buildtools
serverless-stepfunction-workflows
Which workstream does this image/service belong to? e.g. persistence
devops
Which branch is the mainline branch? e.g. master
master
What tier is this serverless application? e.g. tier0, tier1 or tier2
tier2
```
The following folders and file will be built on the repository:

```
./build folder
	bootstrap.sh
	.gitignore
	Jenkinsfile
	.ci.yml

Jenkinsfile
```
Then push the code to make a pull request to merge the changes into the master branch. 

2. Check onboarding and duild a branch onto the CICD pipeline

Go to https://prod1.jenkins.lifion.oneadp.com/view/DEVOPS-CI/  <br>

This shows CICD enabled for sereverless-stepfunction-workflows.  <br>

Note: It may take around 10 minutes for the job to show up. <br>

![](../saved-images/DEVOPS-CI.png)

From: https://prod1.jenkins.lifion.oneadp.com/view/DEVOPS-CI/ <br>

Click on sereverless-stepfunction-workflows. In this case, an application repository is a job. <br>

See all the branches in the jobs. Each branch has its build, which is a CICD pipeline. <br>

![](../saved-images/serverless-stepfunction-workflows-prod1.png)

From: https://prod1.jenkins.lifion.oneadp.com/view/DEVOPS-CI/job/devops-serverless-stepfunction-workflows/   <br>

Right now there is no builds for the master branch. <br>

![](../saved-images/build1.png)

From: https://prod1.jenkins.lifion.oneadp.com/view/DEVOPS-CI/job/devops-serverless-stepfunction-workflows/job/master/

First time will only see “Build Now”, but after you first build it. I will show “Build with Parameters”.

Click on “Build Now”, it will start building the branch onto the pipeline. 

![](../saved-images/build2.png)
 
From: https://prod1.jenkins.lifion.oneadp.com/view/DEVOPS-CI/job/devops-serverless-stepfunction-workflows/job/master/

As you can see, the branch is building onto the CICD pipeline. To see what these preconfigured stages are, go to this documentation: https://cicd.lifion.oneadp.com/docs/sls_ci_cd


If you start another build, the parameter will look such as: 

![](../saved-images/build3.png)

### How to debug errors on console output: 

Go to the bottom left hand corner of https://prod1.jenkins.lifion.oneadp.com/view/DEVOPS-CI/job/devops-serverless-stepfunction-workflows/job/master/  <br>
Click on one of the red crosses enclosed with red circle. <br>

You will see a Console for debugging it: 

![](../saved-images/serverless-stepfunction-workflows-prod1.png)
