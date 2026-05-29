Use the service ELASTIC Container register (ECR)
HERE Following Commands are :

Make sure that you have the latest version of the AWS CLI and Docker installed. For more information, see Getting Started with Amazon ECR .
Use the following steps to authenticate and push an image to your repository. For additional registry authentication methods, including the Amazon ECR credential helper, see Registry Authentication .

1.Retrieve an authentication token and authenticate your Docker client to your registry. Use the AWS CLI:
aws ecr get-login-password --region us-east-1 | docker login --username AWS --password-stdin 631164543894.dkr.ecr.us-east-1.amazonaws.com
Note: If you receive an error using the AWS CLI, make sure that you have the latest version of the AWS CLI and Docker installed.

2.Build your Docker image using the following command. For information on building a Docker file from scratch see the instructions here . You can skip this step if your image is already built:
docker build -t expense/backend.

3.After the build completes, tag your image so you can push the image to this repository:
docker build -t 
docker tag expense/backend:latest 631164543894.dkr.ecr.us-east-1.amazonaws.com/expense/backend:latest.

4.Run the following command to push this image to your newly created AWS repository:
docker push 631164543894.dkr.ecr.us-east-1.amazonaws.com/expense/backend:latest