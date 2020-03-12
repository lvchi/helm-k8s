## Install helm

wget https://storage.googleapis.com/kubernetes-helm/helm-v2.14.1-linux-amd64.tar.gztar -xzvf helm-v2.14.1-linux-amd64.tar.gzsudo mv linux-amd64/helm /usr/local/bin/helm

## Verify Helm Package

helm -h

## Verify Where it deployed

kubectl get pods -n kube-system



## Serch for some application like

helm search <Application Name>



## Install Application via Helm

helm install <Application Name>

- Each installation of a Helm chart to your cluster is referred to as a release.

- With Helm it’s easy to have multiple releases installed to a single cluster, each with its own specific configuration.



helm install --name <releasename> <ApplicationName>

---------------------------------------------------
Text Direction : Create & Deploy HELM Chart on Cluster
##Create HELM Chart

- helm create <chart-name>

- Name of the chart provided here will be the name of the directory where the chart is created and stored.



```

Let's understand the relevance of these files and folders created for us:



Chart.yaml: This is the main file that contains the description of our chart

values.yaml: this is the file that contains the default values for our chart

templates: This is the directory where Kubernetes resources are defined as templates

charts: This is an optional directory that may contain sub-charts

```



##HELM Commands for Chart

- helm lint <chart-full-path>

#This is a simple command that takes the path to a chart and runs a battery of tests to ensure that the chart is well-formed



- helm template <chart-full-path>

#This will generate all templates with variables without a Tiller Server, for quick feedback, and show the output. Now that we know everything is OK, we can deploy the chart:





- helm install --name <release-name> <chart-full-path>

#Run this command to install the chart into the Kubernetes cluster:

Text Direction : Upload HELM Chart in S3 Bucket
#AWS CLI Credentials must be Set on Machine

#Verify

aws sts get-caller-identity



#Create Chart in S3 Bucket

Execute Shell Script: File is attached as PDF on above Lecture

./s3-helm-repo.sh



#List all Repos

helm repo list



#Export AWS Region in Variable

export AWS_REGION=ap-south-1



#Package your Charts

helm package hello-world



#Upload your helm package

helm s3 push <tar-file> <s3chart-name>



#Search for your repository

helm search <repo-name>