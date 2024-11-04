---
title:  Dashboard
layout: default
parent: Ek Araçlar
---

# Dashboard

[Kullanılabilecek farklı tagler](https://github.com/kubernetes-sigs/kubespray/blob/master/docs/ansible.md)

### Dashboard alternatif kurulum

[Buradaki kurulum](https://github.com/kubernetes/dashboard) ile kurulur. 

### Dışarıdan Erişim için Nodeport Tanımı

```sh
kubectl edit -n kube-system   svc kubernetes-dashboard

...
  type: ClusterIP
...

# =>
...
  type: NodePort
... 

# aynı dosyada aşağıdaki satır altına yeni bir satır ekliyoruz.
...
    targetPort: 8443
...

#=>
...
    targetPort: 8443
    nodePort: 30333
...
```
### Dashboard için admin kullanıcı oluşturma

[Buradaki kurulum](https://github.com/kubernetes/dashboard/blob/master/docs/user/access-control/creating-sample-user.md) ile tam yetkili kullanıcı oluşturulur.

```yaml

apiVersion: v1
kind: ServiceAccount
metadata:
  name: admin-user
  namespace: kubernetes-dashboard

---

apiVersion: rbac.authorization.k8s.io/v1
kind: ClusterRoleBinding
metadata:
  name: admin-user
roleRef:
  apiGroup: rbac.authorization.k8s.io
  kind: ClusterRole
  name: cluster-admin
subjects:
- kind: ServiceAccount
  name: admin-user
  namespace: kubernetes-dashboard

---

apiVersion: v1
kind: Secret
metadata:
  name: admin-user
  namespace: kubernetes-dashboard
  annotations:
    kubernetes.io/service-account.name: "admin-user"   
type: kubernetes.io/service-account-token   

```

dashboardta kullanılacak token

```sh
{% raw %}
kubectl get secret admin-user -n kubernetes-dashboard -o jsonpath={".data.token"} | base64 -d
{% endraw %}
```

[dashboard](https://github.com/kubernetes/dashboard/blob/master/docs/images/signin.png)
