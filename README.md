# flask_test
test with gunicorn ngnix flask

## Gunicorn
- Start gunicorn with 
`gunicorn --bind 0.0.0.0:8000 app:app` 
where the file is app.py (first "app" before the colon) and it contains a variable like
`app = Flask(__name__)`

# Nginx
- Nginx cann access gunicorn by accessing the `testproject.sock`, which is is the current folder

See config file.
Has to be linked to `/etc/nginx/sites-enabled/`
