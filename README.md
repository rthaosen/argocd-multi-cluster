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