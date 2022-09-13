https://reflectoring.io/aws-cloudformation-deploy-docker-image/

Creating Network
aws cloudformation create-stack --stack-name reflectoring-hello-world-network   --template-body file://network.yml --capabilities CAPABILITY_IAM

Creating the Service Stack
aws cloudformation create-stack --stack-name reflectoring-hello-world-service --template-body file://service.yml --parameters ParameterKey=StackName,ParameterValue=reflectoring-hello-world-network ParameterKey=ServiceName,ParameterValue=reflectoring-hello-world       ParameterKey=ImageUrl,ParameterValue=docker.io/reflectoring/aws-hello-world:latest       ParameterKey=ContainerPort,ParameterValue=8080       ParameterKey=HealthCheckPath,ParameterValue=/hello       ParameterKey=HealthCheckIntervalSeconds,ParameterValue=90

