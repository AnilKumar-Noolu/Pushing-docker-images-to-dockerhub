# Pushing-docker-images-to-dockerhub

In this Repo, we will be pushing the Docker Images to dockerhub by using Jenkins in Declarative approach.
The only thing we needed here is an EC2 Instance created with Docker and Git installed in it.
And then we can pull docker images or build docker images using Dockerfile and can push them to dockerhub by using Jenkins Pipeline Job.

-> Here we will be using hostname as a string parameter as we need to ssh into the virtual machine opn which the docker is installed, generally the value in hostname will be ec2-user@private_ip of that instance.

->Also [ec2-instance-key-pair] is nothing but the key pair that we use in EC2 instance to login, we will add it to Jenkins by use of Manage Credentials section.
