kubernetes dashboard
======

 - Dashboard是Kubernetes社区官方开发的仪表板,有了仪表板后管理者就能够通过Web-based方式来管理Kubernetes集群,除了提升管理方便,也让资源视觉化,让人更直觉看见系统资讯的呈现结果。

**在master1通过kubectl来建立kubernetes dashboard即可：**

```
kubectl apply -f ExtraAddons/dashboard

kubectl -n kube-system get po,svc -l k8s-app=kubernetes-dashboard
```

***完成后,就可以通过浏览器存取Dashboard***

```
https://{YOUR_MASTERIP}:6443/api/v1/namespaces/kube-system/services/https:kubernetes-dashboard:/proxy/。
```

**复制token,然后贴到Kubernetes dashboard**

```
kubectl -n kube-system describe secrets | sed -rn '/\sdashboard-token-/,/^token/{/^token/s#\S+\s+##p}'
```
