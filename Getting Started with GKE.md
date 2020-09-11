#lab Google Cloud Fundamentals: Getting Started with GKE

#Objectives 
1 Provision a Kubernetes cluster using Kubernetes Engine.

2 Deploy and manage Docker containers using kubectl.

#step1 (gcloud auth list)this command willgive output of an active accont name
nellylynn_moyo@cloudshell:~ (bubbly-yeti-289122)$ gcloud auth list
     Credentialed Accounts
ACTIVE  ACCOUNT
*       nellylynn.moyo@gmail.com

To set the active account, run:
    $ gcloud config set account `ACCOUNT`

#step 2 ($ gcloud config list project) this command will list the project ID 
nellylynn_moyo@cloudshell:~ (bubbly-yeti-289122)$ gcloud config list project

#Results
[core]
project = bubbly-yeti-289122
Your active configuration is: [cloudshell-7087]

#step3 ($ export MY_ZONE=us-central1-a) this command will  export the loaction that the applcation is running on in this case it is assigned automatcally by Qwiklabs. If itsa scenarion where you have assigned a loaction you type the location after ZONE= 

nellylynn_moyo@cloudshell:~ (bubbly-yeti-289122)$ export MY_ZONE=us-central1-a
#Results 
nothings prints out 
#step4 ($ gcloud container clusters create webfrontend --zone $MY_ZONE --num-nodes 2) this command will creates  a kubernetes cluster named webfront  with 2 nudes on the specified zone from the previous command 

nellylynn_moyo@cloudshell:~ (bubbly-yeti-289122)$ gcloud container clusters create webfrontend --zone $MY_ZONE --num-nodes 2
#REsults 
WARNING: Warning: basic authentication is deprecated, and will be removed in GKE control plane versions 1.19 and newer. For a list of recommended authentication methods, see
: https://cloud.google.com/kubernetes-engine/docs/how-to/api-server-authentication
WARNING: Currently VPC-native is not the default mode during cluster creation. In the future, this will become the default mode and can be disabled using `--no-enable-ip-ali
as` flag. Use `--[no-]enable-ip-alias` flag to suppress this warning.
WARNING: Newly created clusters and node-pools will have node auto-upgrade enabled by default. This can be disabled using the `--no-enable-autoupgrade` flag.
WARNING: Starting with version 1.18, clusters will have shielded GKE nodes by default.
WARNING: Your Pod address range (`--cluster-ipv4-cidr`) can accommodate at most 1008 node(s).
This will enable the autorepair feature for nodes. Please see https://cloud.google.com/kubernetes-engine/docs/node-auto-repair for more information on node autorepairs.
Creating cluster webfrontend in us-central1-a... Cluster is being health-checked (master is healthy)...done.
Created [https://container.googleapis.com/v1/projects/bubbly-yeti-289122/zones/us-central1-a/clusters/webfrontend].
To inspect the contents of your cluster, go to: https://console.cloud.google.com/kubernetes/workload_/gcloud/us-central1-a/webfrontend?project=bubbly-yeti-289122
kubeconfig entry generated for webfrontend.
NAME         LOCATION       MASTER_VERSION  MASTER_IP     MACHINE_TYPE   NODE_VERSION   NUM_NODES  STATUS
webfrontend  us-central1-a  1.15.12-gke.2   35.188.108.4  n1-standard-1  1.15.12-gke.2  2          RUNNING


#step5  ($ kubectl version)this command will give a version of kubernets the cluster is running on 
nellylynn_moyo@cloudshell:~ (bubbly-yeti-289122)$ kubectl version
#Results 
nellylynn_moyo@cloudshell:~ (bubbly-yeti-289122)$ kubectl version
Client Version: version.Info{Major:"1", Minor:"19", GitVersion:"v1.19.0", GitCommit:"e19964183377d0ec2052d1f1fa930c4d7575bd50", GitTreeState:"clean", BuildDate:"2020-08-26T1
4:30:33Z", GoVersion:"go1.15", Compiler:"gc", Platform:"linux/amd64"}
Server Version: version.Info{Major:"1", Minor:"15+", GitVersion:"v1.15.12-gke.2", GitCommit:"fb7add51f767aae42655d39972210dc1c5dbd4b3", GitTreeState:"clean", BuildDate:"2020
-06-01T22:20:10Z", GoVersion:"go1.12.17b4", Compiler:"gc", Platform:"linux/amd64"}


#step6  (kubectl create deploy nginx --image=nginx:1.17.10 ) this command will create a ngnix container  This use of the kubectl create command caused Kubernetes to create a deployment consisting of a single pod containing the nginx contain

nellylynn_moyo@cloudshell:~ (bubbly-yeti-289122)$ kubectl create deploy nginx --image=nginx:1.17.10

#Results 
deployment.apps/nginx created

#step  (kubectl get pods)this command will give a number of pods the ngnix container that was created has 
nellylynn_moyo@cloudshell:~ (bubbly-yeti-289122)$ kubectl get pods
#Results 

NAME                     READY   STATUS    RESTARTS   AGE
nginx-5f7d5d7689-g525c   1/1     Running   0          93s

#step7  ($ kubectl expose deployment nginx --port 80 --type LoadBalancer)this command will expose the ngnix container to traffic Kubernetes created a service and an external load balancer with a public IP address attached to it it will not change as long as the nginx is still in use for all traffic coming to ths container, results shows if it is exposed 

nellylynn_moyo@cloudshell:~ (bubbly-yeti-289122)$ kubectl expose deployment nginx --port 80 --type LoadBalancer

#Results

service/nginx exposed

#step8 (kubectl get services)this command will show the new service that has been added along with the internal and external IP adress if you Cop the external IP adrress 35.222.56.21 and opne it on a browser you get a welcome to nginx page
nellylynn_moyo@cloudshell:~ (bubbly-yeti-289122)$ kubectl get services
#Results 

NAME         TYPE           CLUSTER-IP      EXTERNAL-IP    PORT(S)        AGE
kubernetes   ClusterIP      10.51.240.1     <none>         443/TCP        8m11s
nginx        LoadBalancer   10.51.249.216   35.222.56.21   80:32343/TCP   47s


#step9 ($ kubectl scale deployment nginx --replicas 3)this command will increase the number of pods on the container to 3 this helps when you need more resources according to the demamd.in this case we will have 3 replicas 
nellylynn_moyo@cloudshell:~ (bubbly-yeti-289122)$ kubectl scale deployment nginx --replicas 3
#Results
deployment.extensions/nginx scaled

#step10 ($kubectl get pods)this command willlist the total number of pods for examke the first time we ran this command it had only 1 now there is 3 

nellylynn_moyo@cloudshell:~ (bubbly-yeti-289122)$ kubectl get pods

#Results
NAME                     READY   STATUS    RESTARTS   AGE
nginx-5f7d5d7689-g525c   1/1     Running   0          5m56s
nginx-5f7d5d7689-zdnj5   1/1     Running   0          60s
nginx-5f7d5d7689-zslsn   1/1     Running   0          60s



