# kubee
Kubernetes creates clusters, deploys and manage clusters.
By using kubernetes we form a cluster ( group of docker containers )
K8S schedules, run and manages isolated containers.
# kubee features
Orchestration
Auto scaling
Auto healing
Master will not take the load as container will be created in nodes/slaves.
Kubernetes commands are always triggered using kubectl.
# Commands
kubectl get nodes == to know how many nodes are present
kubectl get pods == to know how many pods are present/created
kubectl --run image tomcat webserver == tomcat = image name, webserver = pod name
kubectl delete pods pod-name
kuberentes performs container orchestartion by using definition files. Definitions files means yml files.
Definition files, will have 4 top levele elements
1. apiversion: - libraries
2. kind: - can be pod, Replicaset, service etc services/object which we want to create.
3. metadata: - more information about the kuberenets object.
4. spec: docker container related information
To run the definination/yml file - **kubectl create -f xyz.yml**
To know pods - **kubectl get pods**
To know more about pods - **kubctl get pods-o wide**
To delete the pods created - **kubectl delete -f xyz.yml**
To get more information about the pod - **kubectl describe pods pod-name** (pod-name = ngnix-pod,postgres-pod)
to open the ports, gcloud compute firewall-rules create rule11 --allow tcp:8080
                   gcloud compute firewall-rules create rule22 --allow tcp-9090

   ------------------------
II).   **ReplicationController**
   here we can perform load balancibg and scalling.
   E.g.
   Create a replication controller for creating 3 replicas of httpd (web server).
   
   ----ReplicationController is out dated and replaced by replicaSet and which has an additional specification called "selector" field.

   this selecetor uses child element called "matchlabels" , where it will search for pods based on a specific label name and adds them to the clusters.

   E.g. Create a replicaset file to start 4 tomcat replicas and then perform scaling.

vim replica-set.yml
---
apiVersion: apps/v1
kind: ReplicaSet
metadata:
 name: tomcat-rs
 labels:
  author: durgasoft
  type: webserver
spec: 
 replicas: 4
 selector:
  matchLabels: 
   type: webserver
 template:
  metadata:
   name: tomcat-pod
   labels:
    type: webserver
  spec:
  containers:
   - name mywebserver
     image tomcat
     ports:
      - container Port: 80
        hostPort: 9090
...   
   
kubectl create -f replica-set.yml
kubectl get replicaset

**scaling Option 1:** code level
to make changes in the file, go to yml file and perform scaling 4pods to 6pods and then command,

kubectl replace -f replica-set.yml

**scaling Option 2:** command level

kubectl scale --replicas=2 -f replica-set.yml

III). **Service Object:**
used for network load balancing and port mapping
this Oject uses 3 ports,
1. Target port - It is pod or container port
2. port - Refers to service port
3. hostport - Refers to host machine port to make it accessable from external network.

kubectl get all



