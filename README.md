# deploy awebsite

## pre-reqs 

you must have a gcp personal project pre-configured, it is helpful to have gcloud deployed as you will use that to assist in deploying to the cluster with kubectl

## steps

clone the project to your local system

modify the terraform/terraform.tfvars to reflect your gcp project id

modify the terraform/gke.tf to include the cluster password of your choosing

cd into ./terraform and perform 
> terraform init
> terraform plan
> terraform apply




