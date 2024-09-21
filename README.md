[//]: # (https://www.youtube.com/watch?v=s_o8dwzRlu4 : 42:00)

## Setup Kubernetes

Minikube:
```dockerfile
curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
chmod +x minikube-linux-amd64
sudo mv minikube-linux-amd64 /usr/local/bin/minikube
```

Kubectl:
```dockerfile
curl -LO "https://storage.googleapis.com/kubernetes-release/release/$(curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt)/bin/linux/amd64/kubectl"
chmod +x ./kubectl
sudo mv ./kubectl /usr/local/bin/kubectl
```

#### Setting up K8S:
> minikube start --driver=docker  
> minikube status  
> minikube dashboard  
> 
#### Start MongoDB and Webapp
> kubectl apply -f mongo-config.yaml  
> kubectl apply -f mongo-secret.yaml  
> kubectl apply -f mongo.yaml  
> kubectl apply -f webapp.yaml  
> kubectl get all  
> kubectl get configmap  
> kubectl get secret  
> kubectl describe <component-type> <component-name>  
> kubectl get pod  
> kubectl logs webapp-deployment-655ff6696b-g4q7b  
> kubectl logs webapp-deployment-655ff6696b-g4q7b -f   
> kubectl get svc  
> kubectl get node -o wide  
> kubectl get services --all-namespaces -o wide  
> minikube dashboard  
> minikube delete  
> minikube start --driver=docker --ports=30100:30100  

##### SSH in minikube
> minikube ssh  
> sudo ss -tuln | grep 30100 (This will return if any service is listing to this port)  


##### If you can't access the NodePort service webapp with `MinikubeIP:NodePort`, execute the following command:
> minikube service webapp-service  
 
### Test Direct Pod Access (Port Forwarding)
> kubectl port-forward svc/webapp-service 8080:3000  
Now access application with http://localhost:8080/  

### Check services by port
> sudo lsof -iTCP:30100 -sTCP:LISTEN  
> Test-NetConnection -ComputerName localhost -Port 30100 (Verify from windows PS)  
> 