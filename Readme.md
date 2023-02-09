***Create Cluster***

  

```eksctl create cluster --name=eks-planet9 --region=us-east-1 --zones=us-east-1a,us-east-1b --without-nodegroup```

  

***Get List of clusters***

  

```eksctl get cluster```

  

***Template***

```eksctl utils associate-iam-oidc-provider --region region-code --cluster <cluter-name> --approve```

  

***Replace with region & cluster name***

```eksctl utils associate-iam-oidc-provider --region us-east-1 --cluster eks-planet9 --approve```

  

***Create Public Node Group***
```
eksctl create nodegroup --cluster=eks-planet9 \

--region=us-east-1 \

--name=eks-planet9-ng-public1 \

--node-type=t2.medium \

--nodes=2 \

--nodes-min=2 \

--nodes-max=4 \

--node-volume-size=20 \

--ssh-access \

--ssh-public-key=p9-ec2 \

--managed \

--asg-access \

--external-dns-access \

--full-ecr-access \

--appmesh-access \

--alb-ingress-access
```

  

***List EKS clusters***

ls  

 ```eksctl get cluster```

  

**List NodeGroups in a cluster***

  

```eksctl get nodegroup --cluster=eks-planet9```

  

***List Nodes in current kubernetes cluster***

```kubectl get nodes -o wide```

  

***Our kubectl context should be automatically changed to new cluster***

```kubectl config view --minify```

  

***List EKS Clusters***

```eksctl get clusters```

  

***Capture Node Group name***
```
eksctl get nodegroup --cluster=<clusterName>
eksctl get nodegroup --cluster=eks-planet9
```

***Delete Node Group***
```
eksctl delete nodegroup --cluster=<clusterName> --name=<nodegroupName>
```
```
eksctl delete nodegroup --cluster=eks-planet9 --name=eks-planet9-ng-public1
```

  

***Delete Cluster***

  

```
eksctl delete cluster <clusterName>
eksctl delete cluster eks-planet9

```
*Update kubeconfig*
  
```aws eks --region us-east-1 update-kubeconfig --name eks-planet9```


-[FOR yaml Files](https://github.com/itsramkumared/planet9-kubernetes-deployments)

***Planet9 KUBERNETES DEPLOYMENTS YAML FILES***

| S.No | File Name|
| ---- | ------------------- |
| 1.   | Planet9-all |
| 2.   | Planet9 Basics |
| 3.   | database pod |
| 4.   | External RDS |
| 5.   | External RDS-Schema |
| 6.   | Ingress-exp |
| 7.   | EFS & NFS  |
| 8.   | Ingress  |
