# Deploy Flask with gunicorn and nginx


## Create Gunicorn Container
- Create Gunicorn container (see gunicorn/Dockerfile for details) which launches 
`gunicorn --bind 0.0.0.0:8000 app:app` 
where the file is app.py (first "app" before the colon) and it contains a variable like
`app = Flask(__name__)`

## Create Nginx container
-  Create nginx container (see nginx/Dockerfile for details)
- Nginx cann access gunicorn by accessing the `gunicorn-container:80000`, the hostname is specified in the `default.conf` file

## Deploy both containers with docker compose
- `docker-compose build `(rebuilds all images) -> RUN IT EVERYTIME THE BUILD IS CHANGED!!!
- `docker-compose up` (launches containers )

Note: 
- The name of the gunicorn container has to match the proxy_pass hostname in the nginx file, otherwise nginx won't know where to pass the nformation to.
- containers specified in a docker-compose.yaml are by default in the same network + container names are resolved by the internal docker DNS server

