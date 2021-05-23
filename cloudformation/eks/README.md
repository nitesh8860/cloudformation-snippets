#create eksClusterRole

#create cluster with aws cli , bacuase  cloudformation does not allow private endpoint config.

aws eks create-cluster --name project-dev --kubernetes-version 1.16 \
          --role-arn arn:aws:iam::xxxxxxxxx:role/eksClusterRole \
          --resources-vpc-config subnetIds=subnet-0f594303bb2ecbbd8,subnet-823feacb,subnet-22eee57a,subnet-6b09c322,securityGroupIds=sg-3f4f7146,endpointPublicAccess=false,endpointPrivateAccess=true \
          --logging '{"clusterLogging":[{"types":["api","controllerManager"],"enabled":true}]}'


#update kubectl config to access cluster
aws eks --region eu-west-1 update-kubeconfig --name project-dev

kubectl get svc
