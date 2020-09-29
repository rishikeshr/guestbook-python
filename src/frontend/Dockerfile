# -ltUse base Python image from Docker Hub
FROM debian:stretch

# Set the working directory to /app
WORKDIR /app

# Install Python
RUN apt-get update -y && apt-get install python3 -y && apt-get install python3-pip -y

# copy the requirements file used for dependencies
COPY requirements.txt .

# Install any needed packages specified in requirements.txt
RUN pip3 install --trusted-host pypi.python.org -r requirements.txt

# Copy the rest of the working directory contents into the container at /app
COPY . .

COPY appdynamics/ /appdynamics/

#RUN pip3 install --no-index --find-links /app/appdynamics -r /app/appdynamics/requirements.txt
RUN pip3 install http://techcrashcourselab-naa-rj1zkbjt.appd-sales.com:8080/pip/appdynamics-20.8.0.2388-py2.py3-none-any.whl
# Run app.py when the container launches
#ENTRYPOINT ["python3", "front.py"]
CMD pyagent run -- python3 front.py

