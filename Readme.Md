Name: Ammar

Q1:

A developer needs access to view Pods and Services within the `dev` namespace but should not have permissions to modify or delete any resources. How would you create an RBAC policy to meet this requirement?

Task:

Create a Role named `view-pods-services` in the `dev` namespace with the necessary permissions.
Bind this Role to a user named `dev-user`.


Q2:

You are tasked with deploying a memory-intensive application while ensuring resource limits are set appropriately. Perform the following steps:

Create a Deployment named resource-demo with the following specifications:

Use the image busybox.
The container should run the command: ["sh", "-c", "while true; do echo hello; sleep 10; done"].
Set replicas to 3.
Configure resource requests and limits for the containers in the Deployment as follows:

Request 200m of CPU and 256Mi of memory.
Limit the CPU to 500m and memory to 512Mi.
Verify the resource requests and limits are applied by describing the pods created by the Deployment.

Validation Steps:

Ensure the Deployment creates 3 running pods.
Confirm that each pod has the correct resource requests and limits.
Test by stressing the application to ensure the pods respect the defined resource limits.


Q3:

A specific node in your cluster is dedicated to running a critical application and should not accept any other workloads. This node has a taint with `key=dedicated`, `value=critical`, and e`ffect=NoSchedule`. Ensure that only the pods from a deployment named `critical-app` are allowed to run on this node.

Task:

Add the necessary tolerations to the `critical-app` deployment to ensure that its pods can run on the tainted node.


Q4:

You need to label a set of nodes to be used by the backend services only. The label should be `role=backend`. After labeling, ensure that a deployment named `backend-app` only schedules pods on nodes with this label.

Task:

Label the nodes with `role=backend`.
Modify the `backend-app `deployment to ensure that its pods are scheduled only on nodes with the `role=backend` label.


Q5:

Execute the following requirements in the prod namespace. Create a new Deployment named app01 using the nginx:latest container image and have it listen on port 80. The deployment should consist of 2 replicas. Create a new Service named app01-svc and expose the newly created deployment using a NodePort. Confirm that you can access the nginx home (index) page using the NodePort service.



Q6:

You are responsible for deploying and managing a Kubernetes cluster. One of the services running on your cluster is experiencing DNS resolution issues. You suspect that the issue may be related to the configuration of CoreDNS, the default DNS provider in Kubernetes. Using kubectl, please perform the following diagnostic tasks:

Identify the version of CoreDNS currently running on the cluster and save the version into the file /home/ubuntu/coredns/version.txt. 


Q7:

A team needs a persistent storage solution for their database application running in Kubernetes. They require a 1Gi volume that should persist even if the pod is deleted or rescheduled. The storage class used should be fast-storage.

Task:

Create a PersistentVolume (PV) with a size of 1Gi and a fast-storage storage class.
Create a PersistentVolumeClaim (PVC) that binds to this PV and ensure that a pod named database-app uses this PVC for its storage.


Q8:

Create a Kubernetes namespace `finance` with a deployment named `billing-app` using image `traefik:v3.3.0-rc2`. The `billing-app` deployment should only allow inbound traffic from pods in the `web` namespace. All other traffic should be denied.

Task:

Create a NetworkPolicy in the `finance` namespace to enforce this rule.


Q9:

You need to expose a web application running in your cluster to the internet. The application is accessible via a service named `web-service` in the `default` namespace on port 80. The domain name for the application is `example.com`.

Task:

Create an Ingress resource that routes traffic from `example.com` to the `web-service` on port 80.



Q10:

Create a deployment named frontend-app with a nginx image with 1 replica in the frontend namespace that experiences fluctuating traffic. You want to ensure that the number of pods automatically scales based on CPU utilization. The desired CPU utilization target is 60%, with a minimum of 2 pods and a maximum of 10 pods.

Task:

Configure Horizontal Pod Autoscaling (HPA) for the frontend-app deployment to meet these requirements.


Q11:

Your Kubernetes cluster uses ETCD as the key-value store for all cluster data. You need to create a backup of the ETCD data and then simulate a failure by restoring the backup.

Task:

Create a snapshot of the ETCD data and save it to /var/backups/etcd-snapshot.db.
Simulate an ETCD failure by restoring the cluster from the backup you created.


Q12:

Create a deployment named data-processing with redis image that requires all its pods to be scheduled on the same node for data locality reasons. However, it should not be scheduled on the same node as another deployment that you are going to create name web-server with an httpd image.

Task:

Configure the data-processing deployment with a Pod Affinity rule to ensure all its pods are scheduled on the same node.
Add a Pod Anti-Affinity rule to prevent data-processing pods from being scheduled on the same node as web-server.


Q13:

You need to upgrade your Kubernetes cluster from version the current version to version 1.31.1. Ensure that the control plane components are upgraded first, followed by the worker nodes.

Task:

Upgrade the Kubernetes control plane to version 1.31.1.
Upgrade the worker nodes to version 1.31.1 while minimizing downtime.

Q14:

You are tasked with deploying an NGINX-based application in a Kubernetes cluster. Follow the steps below:

Create a Deployment named nginx-deployment using the image nginx:1.21 with 2 replicas.
Expose the Deployment using a Service named nginx-service of type NodePort on port 80.
Create an Ingress named nginx-ingress to route traffic to the nginx-service. The Ingress should:
Use the hostname nginx.example.com.
Route traffic on path / to the nginx-service.
Verify the Ingress configuration by describing the Ingress object.
Validation Steps:

Check that the Deployment is running with 2 pods.
Ensure the Service is correctly exposed on a NodePort.
Verify that the Ingress routes traffic to the application by testing the hostname nginx.example.com.


Q15:

You are implementing a blue-green deployment strategy for an application. Perform the following tasks:

Create two Deployments:
app-blue using the image nginx:1.20 with 1 replica.
app-green using the image nginx:1.21 with 1 replica.
Expose both Deployments using two separate Services:
app-blue-service on port 80.
app-green-service on port 80.
Create an Ingress named app-ingress to:
Initially route traffic to app-blue-service using the hostname app.example.com.
Update the Ingress to route traffic to app-green-service after testing.
Confirm the traffic switch by testing the hostname app.example.com and ensuring it points to the correct version of the application.
Validation Steps:

Verify both Deployments and Services are running correctly.
Confirm the Ingress routes traffic to app-blue-service initially.
Ensure the traffic is switched to app-green-service by updating the Ingress.



Q16:

You have deployed a new version of an application using a Deployment named `myapp` in the `production` namespace. The Deployment creates pods that listen on port 8080. You need to expose this application to external traffic so that it can be accessed via a `LoadBalancer` on port 80.

Task:

Create a Service of type `LoadBalancer` named `myapp-service` that exposes the `myapp` Deployment on port 80 and routes traffic to port 8080 on the pods.
Ensure that the service is accessible from outside the cluster.


Q17:

Create a Deployment name `web-app` with httpd:latest image in the `staging` namespace. You need to roll out an update to httpd:bookworm of the application. Ensure that the rollout is monitored, and if there are any issues, you should be able to roll back to httpd:latest.





