# ngrok
ngrok agent for proxying Jenkins webhook calls from Github

## Usage
* Create `.env` file to pass ngrok tunnel details to container. For example:
```
NGROK_AUTHTOKEN=0HzRyKRmsr720MoafwpuHkJftxc5NOovvz4ANUsj
GITHUB_WEBHOOK_SECRET=M@uNS0F@wqL2
JENKINS_URL=https://jenkins.mycompany.com
```

### docker-compose
* Run `docker-compose up -d`
* Navigate to `http://localhost:4040` to access ngrok agent

### Kubernetes
```
kubectl create configmap ngrok --from-env-file=.env
kubectl create secret generic ngrok --from-env-file=.secrets
kubectl apply -f manifest.yml
```