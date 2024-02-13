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
   **ReplicationController**
   here we can perform load balancibg and scalling.
   E.g.
   Create a replication controller for creating 3 replicas of httpd (web server).
   
   
