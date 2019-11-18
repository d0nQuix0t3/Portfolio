# Create Docker Image and Upload to Docker Hub

---

### Dockerfile

#### Example: Base Python Data Science

``` dockerfile
FROM python:3.7-slim-buster
RUN apt-get update && apt-get upgrade -y
ADD requirements.txt /requirements_python/
WORKDIR /requirements_python
RUN pip3 install --upgrade setuptools
RUN pip3 install -r requirements.txt
```



---

### docker login

``` 
docker login --username=yourhubusername --password=yourpassword 
```

* *Replace **yourhubusername** with your Docker Hub username*
* *Replace **yourpassword** with your Docker Hub password*

``` bash
docker login --username=docker_example --password=docker_password
```



---

### docker build

##### Build and Tag Docker Image

```bash
docker build -t $DOCKER_USERNAME/$DOCKER_IMAGE_NAME:$IMAGE_TAG .
```

* *Replace **$DOCKER_USERNAME** with your Docker Hub username*
* *Replace **$DOCKER_IMAGE_NAME** with name of Docker Image*
* *Replace **$IMAGE_TAG** with custom tag to describe Docker Image*

```bash
docker build -t docker_user/image_name:image_tag .
```



---

### docker push

Run the following command to check for available docker images

```bash
docker images
```

This will print the list of docker images available on your computer.

```bash
REPOSITORY             	 TAG                 IMAGE ID            CREATED             SIZE
docker_user/image_name   image_tag           25f24db9a399        4 minutes ago       682MB
python                 	 3.7-slim-buster     b5a7c089ece3        3 weeks ago         179MB
```

Finally, once you have identified your image, push your docker image to Docker Hub

``` bash
sudo docker push docker_user/image_name:image_tag
```



---

### docker pull

Download docker image

```bash
docker pull docker_user/image_name:image_tag
```

Run image with interactive terminal enabled to keep the STDIN open

```bash
docker run --interactive --tty  docker_user/image_name:image_tag
```



