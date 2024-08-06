# terraform_ec2_jenkins with instalatio of tools like docker, terraform, aws, eksctl, kubectl
Initialize the backend by running the below command

cd terraform_ec2_jenkins
terraform init
Run the below command to check the syntax error

terraform validate 
Run the below command to get the blueprint of what kind of AWS services will be created.

terraform plan -var-file=variables.tfvars
Now, run the below command to create the infrastructure on AWS Cloud .

terraform apply -var-file=variables.tfvars -auto-approve
After Infrastructure Provisioning Complete get the EC2 Public IP and Connect to it using SSH by the Below Command
ssh -i private-key.pem ubuntu@public-ip
- Some times it return with permission denied publicky ERROR The Solution :
sudo chmod 600 private-key.pem
After SSH To EC2 Ensure the Jenkins is Running :

sudo systemctl status jenkins.service
We have installed some services such as Jenkins, Docker, Sonarqube, Terraform, Kubectl, AWS CLI, and Trivy.

Let’s validate whether all our installed or not.

jenkins --version
docker --version
docker ps
terraform --version
kubectl version
aws --version
trivy --version
eksctl --version

Now, we have to configure Jenkins. So, copy the public IP of your Jenkins Server and paste it on your favorite browser with an 8080 port.

To get Jenkins Password
sudo cat /var/lib/jenkins/secrets/intialAdminPassword
