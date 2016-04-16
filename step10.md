# 10. Explore the Kubernetes Dashboard (optional)

Estimated time: 7 min remaining

While logged into the cloud console:

Get the admin password
```sh
$ gcloud container clusters describe hello-world | egrep "password"
    password: vUYwC5ATJMWa6goh
```

Get the dashboard URL
```sh
$ kubectl cluster-info
kubectl cluster-info
Kubernetes master is running at https://107.39.81.152
GLBCDefaultBackend is running at https://107.39.81.152/api/v1/proxy/namespaces/kube-system/services/default-http-backend
Heapster is running at https://107.39.81.152/api/v1/proxy/namespaces/kube-system/services/heapster
KubeDNS is running at https://107.39.81.152/api/v1/proxy/namespaces/kube-system/services/kube-dns
kubernetes-dashboard is running at https://107.39.81.152/api/v1/proxy/namespaces/kube-system/services/kubernetes-dashboard
```
Navigate to the URL that is shown under after `kubernetes-dashboard is running at` and log in with 
username “admin” and the password retrieved above. Then explore the Kubernetes graphical dashboard.

![dashboard](https://cloud.githubusercontent.com/assets/3506071/14579197/55ea61c8-036e-11e6-92ac-f00dc3463536.png)

#### [Go to step 11](step11.md)
#### [Go back to step 9](step9.md)
