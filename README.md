# Terraform Script For Create Kubernetes Cluster
How to create kubernetes cluster in aws ec2 instance using terraform script.


First thing is you need install aws cli to you current instance.Follow this steps to install aws cli
``` 
$ sudo apt-get update
$ sudo apt install awscli
$ aws configure
``` 

After install aws cli you need install terrform to you current instance.Follow this steps to install terraform 
``` 
$ sudo apt-get update
$ wget https://releases.hashicorp.com/terraform/0.12.21/terraform_0.12.21_linux_amd64.zip
$ sudo apt-get install unzip
$ sudo unzip ./terraform_0.11.13_linux_amd64.zip -d /usr/local/bin/
$ terraform -v
``` 

Execute below mention command to create "main.tf".In here you can change "namespace" , "stage" , "name" , "cluster_name" ,
"parent_zone_name" , "zone_name" and "region" variables before execute terraform script.
``` 
cat >> main.tf << EOF
module "kops" {
  source           = "git::https://github.com/kumindu/terraform-kubernetes.git?ref=master"
  namespace        = "owc"
  stage            = "prod"
  name             = "openwitclub-kops"
  cluster_name     = "us-east-1"
  parent_zone_name = "openwit.club"
  zone_name        = "$${name}.$${parent_zone_name}"
  region           = "us-east-1"
}
EOF
```
Type below mention command execute terraform script
``` 
$ terraform init
$ terraform plan
$ terraform apply

```

If you need destroy you kubernetes cluster type below mention command

``` 
$ terraform destroy

```

