# helm-practice 

* Helm is a package manager in Kubernetes, we can use helm to templatize the manifest files or we can manage the application using helm
* With helm we can deploy third party applications like drivers, prometheous, graphana, metrics servers, install all using helm
* Helm contains important files like Chart.yaml, values.yaml, templates folder
* We can give place holders like .Value.deployment.imageVersion

* Sample nginx deployment using helm

* helm install nginx . --> to install package nginx name is there in Chart.yaml

* helm list --> to see all helm charts

[ ec2-user@ip-172-31-79-230 ~ ]$ helm list
NAME    NAMESPACE       REVISION        UPDATED                                 STATUS          CHART           APP VERSION
nginx   default         4               2025-05-18 03:25:50.671203845 +0000 UTC deployed        nginx-0.0.2


* if any changes in image like new image change version in Chart.yaml 0.0.1 to 0.0.2 

* helm upgrade  nginx .  --> to update if any changes are there

* helm history nginx  --> to see all helm deployments

[ ec2-user@ip-172-31-79-230 ~ ]$ helm history nginx
REVISION        UPDATED                         STATUS          CHART           APP VERSION     DESCRIPTION
1               Sun May 18 03:09:29 2025        superseded      nginx-0.0.1                     Install complete
2               Sun May 18 03:18:40 2025        superseded      nginx-0.0.1                     Upgrade complete
3               Sun May 18 03:21:05 2025        superseded      nginx-0.0.1                     Upgrade complete
4               Sun May 18 03:25:50 2025        deployed        nginx-0.0.2                     Upgrade complete

* helm rollback ngin --> roll back to previous deployment or previous one

* helm rollback nginx 4 --> roll back to specific revison

[ ec2-user@ip-172-31-79-230 ~ ]$ kubectl get svc
NAME         TYPE           CLUSTER-IP      EXTERNAL-IP                                                               PORT(S)        AGE
kubernetes   ClusterIP      10.100.0.1      <none>                                                                    443/TCP        70m
nginx        LoadBalancer   10.100.123.85   a000ffb87e9e24fb88a144b402c17099-1053738019.us-east-1.elb.amazonaws.com   80:31363/TCP   22m

http://a000ffb87e9e24fb88a144b402c17099-1053738019.us-east-1.elb.amazonaws.com/ --> to access the application

* helm uninstall nginx --> to uninstall nginx

