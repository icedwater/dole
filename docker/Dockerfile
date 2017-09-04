#! /usr/bin/env docker

# Take a slim copy of the official Python runtime.
FROM python:2.7-slim

# Define /app as a working directory and dump . into it.
WORKDIR /app
ADD . /app

# Make sure requirements (as defined) are installed.
RUN pip install -r requirements.txt

# Let external applications connect here using port 80.
EXPOSE 80

# Set environmental variables here.
ENV NAME world

# Start this when the container launches.
CMD ["python", "app.py"]

