# ngrok
ngrok agent for proxying Jenkins webhook calls from Github

## Usage
* Create `.env` file to pass ngrok tunnel details to container. For example:
```
JENKINS_URL=https://jenkins.mycompany.com
NGROK_DOMAIN=prime-walleye-harmless.ngrok-free.app
```
* Create `.secrets` file to pass secrets/tokens to container. For example:
```
NGROK_AUTHTOKEN=0HzRyKRmsr720MoafwpuHkJftxc5NOovvz4ANUsj
GITHUB_WEBHOOK_SECRET=M@uNS0F@wqL2
NGROK_API_KEY=DvKwKD1ivnB4BoKK3nVLPAGRYDquKez0sCqU5FNv
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