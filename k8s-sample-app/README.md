Simple guestbook app for testing kubernetes cluster. Based on https://kubernetes.io/docs/tutorials/stateless-application/guestbook/.
```
kubectl apply -f redis-leader-deployment.yml 
kubectl apply -f redis-leader-service.yml 
kubectl apply -f redis-follower-deployment.yml 
kubectl apply -f redis-follower-service.yml 
kubectl apply -f frontend-deployment.yml 
kubectl apply -f frontend-service.yml 
kubectl port-forward svc/frontend 8000:80
```
Guestbook application will be listening on http://localhost:8000