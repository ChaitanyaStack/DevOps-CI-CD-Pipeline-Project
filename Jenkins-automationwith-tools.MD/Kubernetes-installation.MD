# Kubernetes Setup on AWS with eksctl

This documentation provides comprehensive instructions on setting up a Kubernetes cluster on Amazon Web Services (AWS) using eksctl, a simple CLI tool for creating clusters on AWS Elastic Kubernetes Service (EKS). eksctl allows you to provision a fully-managed Kubernetes cluster quickly, leveraging AWS's security, reliability, and scalability.

## Prerequisites

Before you begin, make sure you have the following prerequisites installed and configured from AWS CLI,EKSCTL, KUBECTL installation guides:

AWS CLI: https://docs.aws.amazon.com/cli/latest/userguide/cli-chap-install.html

eksctl: https://docs.aws.amazon.com/eks/latest/userguide/eksctl.html

kubectl: https://kubernetes.io/docs/tasks/tools/install-kubectl

Additionally, ensure that your AWS account has the necessary permissions to create EKS clusters and related resources.

## Step 1: Configure AWS CLI

First, configure the AWS CLI with your credentials. Run the following command and follow the prompts:

aws configure

Enter your AWS Access Key ID, Secret Access Key, region, and output format when prompted.

## Step 2: Create a Kubernetes Cluster with eksctl

To create a new Kubernetes cluster, use the following eksctl command. Replace <cluster-name> with your desired cluster name:


eksctl create cluster --name <cluster-name> --version 1.21 --region us-west-2 --nodegroup-name standard-workers --node-type t3.medium --nodes 3

This command creates a Kubernetes cluster named <cluster-name> with three t3.medium nodes in the us-west-2 region.

## Step 3: Configure kubectl to Connect to Your Cluster

eksctl automatically configures kubectl for you. To verify your configuration and connectivity, run:


kubectl get svc


This command should return the default services in your cluster.

## Step 4: Deploying Applications

With your cluster up and running, you can now deploy applications to it. For a simple example, deploy the Kubernetes dashboard:


kubectl apply -f #file name#


## Step 5: Accessing the Kubernetes Dashboard

To access the dashboard, you need to create a proxy server that forwards traffic to the dashboard service. Run:


kubectl proxy


Then, access the dashboard at:

http://localhost:8001/api/v1/namespaces/kubernetes-dashboard/services/https:kubernetes-dashboard:/proxy/


## Cleanup

To delete your cluster, use:


eksctl delete cluster --name <cluster-name>




This structure provides a foundational guide to setting up Kubernetes on AWS using eksctl.
