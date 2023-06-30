# Project Description: Deploying a Toxic Service on AWS with Load Balancer
This project aims to deploy a toxic service using AWS services. The toxic service will be containerized using Docker and will be run on EC2 instances.  Additionally, an Application Load Balancer (ALB) will be set up to distribute incoming traffic between the EC2 instances.
- This Docker image allows access to the Detoxify project via an HTTP API using Flask. It calculates profanity ratings for any given text and requires no additional configuration.
  ___
## Steps to make docker image from toxic_comment:
1. Clone the project to your local machine by using the git clone command.
2. Open a command prompt or terminal and navigate to the project directory.
3. Build the Docker image by running the command 
> ***docker build --pull -t toxictest:latest .***
-  This will pull the necessary dependencies and create the image.
4. After the build is completed, run the Docker container using the command 
> ***docker run -p 5000:5000 toxictest:latest***
- This will start the container and map port 5000 of your local machine to port 5000 of the container.
5. Once the container is running, open a new command prompt or terminal.
6. Test the service by running the following command: 
> ***curl -i -X POST -H 'Content-Type: application/json' -d '{"text": "You are moron"}' http://127.0.0.1:5000/results*** 
- This command sends a POST request to the running service with the provided input text.
7. The expected output should be: {'toxicity': 0.9662318, 'severe_toxicity': 0.015923576, 'obscene': 0.47188887, 'threat': 0.0010962454, 'insult': 0.90948385, 'identity_attack': 0.0132479565}
8. Verify that the output matches the expected values, indicating that the service is working correctly.
If necessary, you can make any modifications or updates to the project code on your local machine and repeat the steps starting from the build step to test the changes.
___
        https://github.com/Egordevs/AWS-Project/issues/1#issue-1782314051

##                     Project Steps:
1. Create an Elastic Container Registry (ECR) repository on AWS to store the toxic service image.
2. Upload the toxic service image to the ECR repository.
3. Set up a small EC2 instance ***(t3.small with 25Gb volume will be enough)*** with Docker installed to run the toxic service container.
4. Open the security group for the EC2 instances to allow HTTP access on port 5000 from all IP addresses.
5. Download the toxic service image from the ECR repository to the newly created EC2 instance.
6. Run the container on the EC2 instance to start the toxic service.
7. Verify that you can send curl requests to the toxic service on the EC2 instance.
8. Duplicate the EC2 instance using an AWS function to obtain two identical machines.
9. Create an Application Load Balancer (ALB) to distribute traffic between the EC2 instances.
10. Register the EC2 instances as targets in the Load Balancer.
Verify that you can successfully make curl requests to the toxic service through the Load Balancer.
_____
## Usage
- To use this project, follow the steps outlined above to deploy the toxic service on AWS with a Load Balancer. Ensure that you have the necessary AWS credentials and access rights to create and configure the required services.

