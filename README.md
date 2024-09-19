# deploy awebsite

## pre-reqs 

you must have a gcp personal project pre-configured, it is helpful to have gcloud deployed as you will use that to assist in deploying to the cluster with kubectl

## steps

clone the project to your local system

modify the terraform/terraform.tfvars to reflect your gcp project id

modify the terraform/gke.tf to include the cluster password of your choosing

cd into ./terraform and perform 
- terraform init
- terraform plan
- terraform apply

cluster will build

navigate to the UI to obtain your cluster api access info and confirm api connection
-kubectl get nodes

cd ./kubernetes

make the devops-tools namespace
- kuebectl create namespace devops-tools

review manifest for desired ports and apply the deployment
- kubectl apply -f awebsite.yaml

review pod deployments
- kubectl get pods -n devops-tools --selector=app=awebsite

once pods are deployed, check the service info
- kubectl get services -o wide -n devops-tools

if you have a system on the same vpc you should be able to hit the website on the nodeport (any node address) of the cluster, with te port identified above.

you can also use kubectl to forward the service to your localhost 
- ex.  kubectl port-forward deployment/awebsite01 31002:31003 -n devops-tools

http://127.0.0.1:31003 should display intended result
- thiswebsite: is cool

