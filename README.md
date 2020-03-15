# Terraform Script For Create Kubernetes Cluster 
Create kubernetes cluster in aws ec2 instance 


``` 
sudo apt-get update
sudo apt install awscli
aws configure
``` 

``` 
$sudo apt-get update
$wget https://releases.hashicorp.com/terraform/0.12.21/terraform_0.12.21_linux_amd64.zip
$sudo apt-get install unzip
$sudo unzip ./terraform_0.11.13_linux_amd64.zip -d /usr/local/bin/
$terraform -v
``` 

Create main.tf past below inside that file
``` 
module "kops" {
  source           = "git::https://github.com/kumindu/terraform-kubernetes.git?ref=master"
  namespace        = "owc"
  stage            = "prod"
  name             = "openwitclub-kops"
  cluster_name     = "us-east-1"
  parent_zone_name = "domain.com"
  zone_name        = "$${name}.$${parent_zone_name}"
  region           = "us-east-1"
}

```
After create above file type this command execute terraform script
``` 
$terraform init
$terraform plan
$terraform apply

```
