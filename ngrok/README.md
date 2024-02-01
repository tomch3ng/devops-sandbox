# ngrok
ngrok agent for proxying Jenkins webhooks

## Usage
* Create `.env` file to pass ngrok authentication token to container. For example:
```
NGROK_AUTHTOKEN=M@uNS0F@wqL2
```
* Run `docker-compose up`