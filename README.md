opensearch-namespace.yaml
Creates the opensearch namespace in Kubernetes.

opensearch-deployment.yaml
Deploys OpenSearch using a StatefulSet with persistent storage.

opensearch-pv.yaml
Defines a Persistent Volume (PV) using AWS EBS storage.

opensearch-pvc.yaml
Defines a Persistent Volume Claim (PVC) to bind with the PV.

opensearch-service.yaml
Exposes OpenSearch externally via a LoadBalancer Service on port 9200.

Deployment Steps
1. Create Namespace

kubectl apply -f opensearch-namespace.yaml

2. Apply Persistent Volume & Claim

kubectl apply -f opensearch-pv.yaml
kubectl apply -f opensearch-pvc.yaml

3. Deploy OpenSearch StatefulSet

kubectl apply -f opensearch-deployment.yaml

4. Expose OpenSearch via LoadBalancer

kubectl apply -f opensearch-service.yaml

5.Check Pod status:

kubectl get pods -n opensearch

6.Check PVC binding:
kubectl get pvc -n opensearch

7.Get LoadBalancer IP:

kubectl get svc -n opensearch

8.Access OpenSearch in browser or via curl:

curl -X GET "http://<EXTERNAL-IP>:9200"
