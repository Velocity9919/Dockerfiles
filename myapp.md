1.Dockerfile - Defines the image:
````
# Set the base image
FROM python:3.8

# Set the working directory
WORKDIR /app

# Copy the current directory contents into the container at /app
COPY . /app

# Install any needed packages specified in requirements.txt
RUN pip install --trusted-host pypi.python.org -r requirements.txt

# Make port 80 available to the world outside this container
EXPOSE 80

# Define environment variable
ENV NAME World

# Run app.py when the container launches
CMD ["python", "app.py"]
````
Building an Image - Use the docker build command to create the image.
````
docker build -t myapp .
````
Instantiating Containers - Run the built image with ````docker run to spawn a container.
````
# Run a single command within a new container
docker run myapp python my_script.py
# Run a container in detached mode and enter it to explore the environment
docker run -d -it --name mycontainer myapp /bin/bash
````

Viewing Containers - The ````docker container ls```` or ````docker ps```` commands display active containers.

Modifying Containers - As an example, you can change the content of a container by entering in via ````docker exec````.
````
docker exec -it mycontainer /bin/bash
````
Stopping and Removing Containers - This can be done using the ````docker stop```` and ````docker rm``` commands or combined with the ````-f``` flag.
````
docker stop mycontainer
docker rm mycontainer
````
Cleaning Up Images - Remove any unused images to save storage space.
````
docker image prune -a
````
