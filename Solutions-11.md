# Solutions for Exercises-10-Kubernetes-on-AWS-EKS

## Exercise 1

**At first I installed EKSCTL to my virtual machine (Linux Mint):**

```bash
ARCH=amd64
PLATFORM=$(uname -s)_$ARCH

curl -sLO "https://github.com/eksctl-io/eksctl/releases/latest/download/eksctl_$PLATFORM.tar.gz"

tar -xzf eksctl_$PLATFORM.tar.gz -C /tmp && rm eksctl_$PLATFORM.tar.gz

sudo install -m 0755 /tmp/eksctl /usr/local/bin && rm /tmp/eksctl

eksctl version
```

**Next I created the cluster itself:**

```bash
eksctl create cluster --name=twn-exercise-11 --node-type=t3.micro --nodes=3 --nodegroup-name=twn-e11-nodes --region=eu-north-1 --kubeconfig=./kubeconfig.twn-e11.yaml
export KUBECONFIG=/home/imre/kubeconfig.twn-e11.yaml
kubectl get node

eksctl create fargateprofile --name twn-e11-fargate --namespace twn-e11 --cluster twn-exercise-11
eksctl get fargateprofile --cluster twn-exercise-11
```

**The new cluster and the Fargate profile:**

![The new cluster and the fargate profile.](Exercise-1-The-Cluster-and-Fargate-Profile.jpg)
