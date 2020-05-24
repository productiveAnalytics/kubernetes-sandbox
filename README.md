# kubernetes-sandbox
Kubernetes (k8s)

Instead of HyperKit on MacOS, use Virtualbox driver.
e.g. minikube start --vm-driver=virtualbox

1. Create Docker image or use existing from Docker registry e.g. ngnix
2. Deplo Pods on Worker nodes : kubectl apply -f pods_ngnix.yaml
3. Create Ingress "service" : kubectl apply -f svc_manifest.yaml 

OR

1. kubectl create deployment hello-node --image=k8s.gcr.io/echoserver:1.4
   - view deployments : kubectl get deployments
   - view pods : kubectl get pods
   - view logs : kubectl get events
   - view configuration : kubectl config view
2. kubectl expose deployment hello-node --type=LoadBalancer --port=8888
   - view services : kubectl get services
3. On Minikube, check out service : minikube service hello-node
   - To see all services : minikube service list
   - To check within the cluster : curl <URL-displayed-by-minikuve-serice-list>
4. To view existing pods & services, first enable add-on metics-server : minikube addons enable metrics-server
   - kubectl get pod,svc -n kube-system
