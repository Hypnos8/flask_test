from python:3
workdir /app

Copy requirements.txt requirements.txt

RUN pip install --no-cache-dir -r requirements.txt

# Copy Sourcecode
copy app.py .
#Only "Add " can copy complete folders!
Add templates ./templates

# Expose gunicorn to port 8000
# best practice: Create another Docker Container with nginx as reverse proxy
CMD ["gunicorn", "--bind", "0.0.0.0:8000", "app:app"]
