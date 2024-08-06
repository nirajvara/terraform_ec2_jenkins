# terraform_ec2_jenkins with installation of tools and command  like docker, terraform, aws, eksctl, kubectl

Do some modifications to the backend.tf file such as changing the bucket name and dynamodb table(make sure you manually created both on AWS Cloud).

Go to the DynamoDB console: https://console.aws.amazon.com/dynamodb/
Click "Create table".
Configure the table:
Table name: Choose a name (e.g., terraform-locks).
Primary key: Set the primary key to LockID (String).


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
