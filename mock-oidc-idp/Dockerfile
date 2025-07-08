# Use the official lightweight Python image.
FROM python:3.12-slim

# Allow statements and log messages to immediately appear in the logs
ENV PYTHONUNBUFFERED True

# Copy local code to the container image
WORKDIR /app
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt
COPY . .

# Set the default port
ENV PORT=8080

# Run the web service on container startup.
CMD gunicorn --bind 0.0.0.0:"${PORT}" app:app
