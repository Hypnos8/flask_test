# Deploy Flask with gunicorn and nginx


## Create Gunicorn Container
- Create Gunicorn container (see gunicorn/Dockerfile for details) which launches 
`gunicorn --bind 0.0.0.0:8000 app:app` 
where the file is app.py (first "app" before the colon) and it contains a variable like
`app = Flask(__name__)`
- `docker build -t flask_gunicorn .`

## Create Nginx container
-  Create nginx container (see nginx/Dockerfile for details)
- Nginx cann access gunicorn by accessing the `gunicorn-container:80000`, where gunicorn-container is the name of the gunicorn container... (wow)
- - `docker build -t flask_nginx .`

## Deploy both containers with docker compose
Note: The name of the gunicorn container has to match the proxy_pass hostname in the nginx file, otherwise nginx won't know where to pass the nformation to.

