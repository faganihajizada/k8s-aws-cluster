# k8s-aws-cluster
Create a Kubernetes Cluster on AWS with Kops

Steps to Follow:

1. First of all we need an AWS account and access keys to start with. Login to AWS console and generate access keys for our user. We can create it from Identity and Access Management. We need grant following permissions to user which we creating:

        AmazonEC2FullAccess 
        AmazonRoute53FullAccess 
        AmazonS3FullAccess 
        AmazonVPCFullAccess

2. Then we need Install AWS CLI. (we'll install it to Linux OS. also you can install it to Mac OS & Windows OS)
 
        for Linux:

        pip install awscli --upgrade --user

3. Let's install Kops.

        curl -LO https://github.com/kubernetes/kops/releases/download/$(curl -s https://api.github.com/repos/kubernetes/kops/releases/latest | grep tag_name | cut -d '"' -f 4)/kops-linux-amd64

        chmod +x kops-linux-amd64

        sudo mv kops-linux-amd64 /usr/local/bin/kops

    Official Installation guide: https://github.com/kubernetes/kops#installing

4. Now Configure the AWS CLI by providing the Access Key, Secret Access Key and the AWS region that you want the Kubernetes cluster to be installed:

        aws configure

        AWS Access Key ID [None]: AccessKeyValue
        AWS Secret Access Key [None]: SecretAccessKeyValue
        Default region name [None]:
        Default output format [None]:

5. Create an AWS S3 bucket for kops. Kops persist its state in S3 Bucket:

        bucket_name=kops-state-store-k8s-planetx echo $bucket_name

        aws s3api create-bucket \ --bucket ${bucket_name} \ --region us-east-1 




