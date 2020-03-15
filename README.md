# Terraform Script For Create Kubernetes Cluster 
Create kubernetes cluster in aws ec2 instance 

``` 
module "kops" {
  source           = "git::https://github.com/kumindu/terraform-kubernetes.git?ref=master"
  namespace        = "eg"
  stage            = "prod"
  name             = "kops-state"
  cluster_name     = "us-east-1"
  parent_zone_name = "domain.com"
  zone_name        = "$${name}.$${parent_zone_name}"
  region           = "us-east-1"
}

```
