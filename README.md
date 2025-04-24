# Prerequisites
kubectl – A command line tool for working with Kubernetes clusters. For more information, see Installing or updating kubectl. https://docs.aws.amazon.com/eks/latest/userguide/install-kubectl.html

eksctl – A command line tool for working with EKS clusters that automates many individual tasks. For more information, see Installing or updating. https://docs.aws.amazon.com/eks/latest/userguide/eksctl.html

AWS CLI – A command line tool for working with AWS services, including Amazon EKS. For more information, see Installing, updating, and uninstalling the AWS CLI https://docs.aws.amazon.com/cli/latest/userguide/cli-chap-install.html in the AWS Command Line Interface User Guide.

After installing the AWS CLI, I recommend that you also configure it. For more information, see Quick configuration with aws configure in the AWS Command Line Interface User Guide. https://docs.aws.amazon.com/cli/latest/userguide/cli-configure-quickstart.html#cli-configure-quickstart-config

Argo CD CLI(Not the actual Argo CD Installation) - https://argo-cd.readthedocs.io/en/stable/cli_installation/#installation

# EKS Setup

## EKS Clusters Creation

eksctl create cluster --name hub-cluster --region us-west-1

eksctl create cluster --name spoke-cluster-1 --region us-west-1

eksctl create cluster --name spoke-cluster-2 --region us-west-1

## EKS Clusters Deletion

eksctl delete cluster --name hub-cluster --region us-west-1

eksctl delete cluster --name spoke-cluster-1 --region us-west-1

eksctl delete cluster --name spoke-cluster-2 --region us-west-1


# Argo CD Setup
## Install Argo CD
commands:
kubectl create namespace argocd

kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml

## Run Argo CD in HTTP Mode(Insecure)
https://github.com/argoproj/argo-cd/blob/54f1572d46d8d611018f4854cf2f24a24a3ac088/docs/operator-manual/argocd-cmd-params-cm.yaml#L82

## Expose Argo CD Server Service in NodePort Mode
command: kubectl edit svc argocd-server -n argocd

and change the type to NodePort from ClusterIP